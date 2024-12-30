# pathbuf utils
## convert path to relative path
```rust
/// if path is absolute path, convert to relative path
/// else return path
pub fn absolute_or_path<P>(path: P) -> PathBuf
where
    P: AsRef<Path>,
{
    let path = path.as_ref();
    dbg!(path);
    path.canonicalize().unwrap().to_path_buf()
}
```
## compare two path is eq
```rust
/// compare two path is equal
/// if is_strict is true, p1,p2 should exist
/// else p1,p2 anyone is not exist is also return true
pub fn is_eq_path<P>(p1: P, p2: P, is_strict: bool) -> bool
where
    P: AsRef<Path>,
{
    match (p1.as_ref().exists(), p2.as_ref().exists()) {
        (true, true) => p1.as_ref().canonicalize().unwrap() == p2.as_ref().canonicalize().unwrap(),
        _ => !is_strict,
    }
}
```