# serde + rmp-serde(msgpack)

## add deps

```toml
serde = { version = "1.0.202", features = ["derive"] }
rmp-serde = "1.3.0"
```
## code

```rust
// ...
use rmp_serde::{Deserializer, Serializer};
use serde::{Deserialize, Serialize};

/// ## Gen compile cache
/// use msgpack to serialize and deserialize
#[derive(Clone, Debug, Serialize, Deserialize)]
pub struct Cache {
    /// cache file path
    path: PathBuf,
    /// current os
    os: String,
    /// compile target, default => makepad
    target: Target,
    /// cache values, key is file path, value is file hash value
    values: Option<HashMap<PathBuf, String>>,
}

impl Cache{
    pub fn read<P>(path: P) -> Result<Cache, Box<dyn Error>>
    where
        P: AsRef<Path>,
    {
        return if path.as_ref().exists() {
            let f = File::open(path)?;
            let mut decode = Deserializer::new(f);
            let cache: Cache = Deserialize::deserialize(&mut decode)?;
            Ok(cache)
        } else {
            // cache file not exist
            Err("cache file not exist".into())
        };
    }

    // create cache file and write cache instance to it
    pub fn write(&self) -> () {
        let cache_path = self.path.as_path();
        let mut file = if !cache_path.exists() {
            // create a new file
            File::options()
                .write(true)
                .read(true)
                .create_new(true)
                .open(cache_path)
        } else {
            File::open(cache_path)
        }
        .expect("cache file create or open failed");

        let mut buf = Vec::new();

        let _ = self.serialize(&mut Serializer::new(&mut buf)).unwrap();

        let _ = file.write(&buf).expect("cache file write failed");

        info("cache file write success")
    }
}
```