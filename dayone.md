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

## Rust Adoption at Amazon

* Key takeaways
  * Have a real reason to use Rust
    * Too high of an org cost
    * Reasons
      * P99/tail latency
      * Memory Usage
      * Cold start time
      * Reliability
    * Parity can be increadibly hard, particuarly with highly optimized, mature codebases
  * Find, grow, and empower Rust pragmatists
  * Learn (or build!) new tools
    * cargo bloat, turmoil
  * Build operational capabilities early
    * Having expert guidance on what tools should be used
      * Flamegraph for 10x cpu improvement
    * Cheapest time to build operational capabilities is during Development
* Examples
  * FireTV started building with Rust after 10x improvement from PoC
    * Strategic rewrites with tight API boundaries/surface areas. Avoid interop with a bunch of languages
    * Social learning
      * Experts learn by teaching, begineers learn from experts - solving real problems (ie. advent of code)
* The Tipping Point
  * Inflection point where it goes from "Do I have to use Rust" -> "When can I start using Rust"
  * Teams w/o Rust expert are 40% more likely to give up
* Teaching Rust is hard
  * Content has to match prev experience
* Learning
  * individual
    * right content, right time
  * social
    * beg learn, teach, etc

## Redis C Rewrite

* migrating is a moving target
  * best to slowly rewrite modules as applicable
* TrieMap - prefix searched and key compression
* decided to start with a functionally equivalent module - same public api, and functionality
  * too slow and memory-hungry
  * tried non-packed
* get rid of unsafe from public api
  * miri as a CI check
  * abuse debug assertions
  * enable clippy options - docs and one unsafe per block
  * design unsafe private apis that are hard to misuse
* about making something more maintainable, tests, benchmarks, docs, etc
* zero copy crate only works if one field is dyn

## Rivian

* dev tool, cloud easiest to play with
* in-vehicle firmware with OS is pretty good
* RTOS/micro can be a lot harrier, esp if not going all in
* don’t lock versions
  * your deps wont do that
* hard on posix vehicle swe
  * monorepos, Bazel/cmake pipeline
  * integrating with existing C++
* embedded (no-std)
  * most are c rather than c++
  * not as much worth it unless you do it all the way
  * safety critical has certifications that rust won’t have 
  * embassy is a good framework, on ATSAMD
  * can we get rid of RTOS and use embassy instead
* kellnr - private crates.io

## Hyperlight Microsoft

* VIRTUAL MACHINE MANAGER
* no OS in guest, 1-2ms
* directly embedded in program 
* seven vulnerabilities from 2022-24 with containers
  * process isolation has a lot of attack surface
  * not good for multi-tenant isolation
* wasm has good features, but not hardened
* can run hypervisor or kvm - these leverage intel / amd virt features 
* hyperlight in rust for library, unmanaged memory, performance, no runtime
* built a c interop so they can run their existing c# tests against the new implementation
* WASM guests work in hyperlight with a WIT (web interface). This provides a RPC framework with rust codegen

## Misc

* https://www.youtube.com/watch?v=UptsQuOlhBU - Oxide
* cargo bloat - reduce artifact size
* tokio turmoil - network chaos testing
* 