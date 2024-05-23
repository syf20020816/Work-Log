# Hash, Eq, PartialEq trait

## example
```rust
/// ## 定root多叉模型树
/// ### struct example
/// ```
/// {
/// node: src/views/root.gen,
/// children: [
///     {node: src/a.gen, children: [
///             {node: src/views/b.gen, children: None},
///             {node: src/views/d.gen, children: None},
///             {node: src/components/c.gen, children: None}
///         ]
///     },
///   ]
/// }
/// ```
#[derive(Debug, Clone)]
pub struct ModelTree {
    /// model node can be widget or rs file, but the root node must be widget
    pub node: ModelNode,
    pub children: Option<HashSet<ModelTree>>,
}

impl PartialEq for ModelTree {
    fn eq(&self, other: &Self) -> bool {
        // self.node.source().unwrap().eq(other.node.source().unwrap())
        self.node == other.node
    }
}

impl Eq for ModelTree {}

impl Hash for ModelTree {
    fn hash<H: std::hash::Hasher>(&self, state: &mut H) {
        self.node.hash(state);
    }
}
```