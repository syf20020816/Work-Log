# macro rule

## from_struct_to_ptr

```rust
#[macro_export]
macro_rules! from_struct_to_ptr {
    ($ptr: ty, $field: expr, $field_ty: expr) => {
        impl From<&ItemStruct> for $ptr {
            fn from(value: &ItemStruct) -> Self {
                // 将GenUI的结构体转为Makepad的属性结构体
                let mut new_item = quote_makepad_widget_struct(value);
                // 设置#[deref]给当前的属性结构体
                if let Fields::Named(fields) = &mut new_item.fields {
                    // add view
                    fields
                        .named
                        .push(struct_field(vec!["deref"], $field, $field_ty));
                }
                Self(new_item)
            }
        }
    };
}
```

## ptr_to_token

```rust
#[macro_export]
macro_rules! ptr_to_token {
    ($ptr: ty) => {
        impl ToToken for $ptr {
            fn to_token_stream(&self) -> TokenStream {
                self.0.to_token_stream()
            }
        }
    };
}
```

## Replace

```rust
use proc_macro2::TokenStream;
use quote::ToTokens;
use syn::{Fields, ItemStruct};

use crate::{from_struct_to_ptr, ptr_to_token, utils::struct_field, widget::utils::quote_makepad_widget_struct, ToToken};

pub struct IconPropPtr(pub ItemStruct);

// impl From<&ItemStruct> for IconPropPtr {
//     fn from(value: &ItemStruct) -> Self {
//         // 将GenUI的结构体转为Makepad的属性结构体
//         let mut new_item = quote_makepad_widget_struct(value);
//         // 设置#[deref]给当前的属性结构体
//         if let Fields::Named(fields) = &mut new_item.fields {
//             // add view
//             fields
//                 .named
//                 .push(struct_field(vec!["deref"], "icon", "Icon"));
//         }
//         IconPropPtr(new_item)
//     }
// }

from_struct_to_ptr!{IconPropPtr, "icon", "Icon"}
// impl ToToken for IconPropPtr {
//     fn to_token_stream(&self) -> TokenStream {
//         self.0.to_token_stream()
//     }
// }
ptr_to_token!(IconPropPtr);
```