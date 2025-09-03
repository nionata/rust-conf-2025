# Day One

https://rustconf.com/schedule/#wednesday

## Microsoft Key note

* Declared c/c++ deprecated in a Tweet
  * Got an email from microsoft CEO
* Sponsor RustTLS
* Rust in Windows Kernel
  * GDI region - shipping in windows systems
  * Crash / memory bug was very explicit and exited out
* Windows drivers FFI
* multi-tier index for meaningful info retrieval (MIMIR)
  * semantic indexer and search
  * from office
* Azure
  * Caliptra - hardware root of trust
  * Boost agents - VM agent
  * Hyper-V - instruction emulation, virtualization
  * Open VMM - virtual machine monitor
  * HyperLight - micro-VM, low latency minimal overhead, 
  * Azure rust sdk
* microsoft/rust-guidelines
* Migration
  * Graph RAG and translator - helping translate and migrate codebase
  
## Solona

* Writing a lot of libraries in RUST
* SOL uses QUIC + jsonRPC
* 

## Carbon

* Greenfield <> Brownfield spectrum
  * Rust interop is currently on the left
    * Smaller, tighter API surface, far more constrained with c/c++ lang features
  * Migrating exisitng large C++ codebases is on the right
    * Large API surface, deep usageo f language features
* Carbon is explicilty targeting brownfield
  * Every design decision tradeoff goes the way of interop with c++ lang features (ie. templates, overloading, inheritence)
  * They are adding memory safety
    * C++ lang standards team explicitly does not want to adopt memory safety approaches
* 

## Misc

* https://www.youtube.com/watch?v=UptsQuOlhBU - Oxide