Carousel
===

An open source docker container / kubernetes pod management tool that allowed to spin
new containers / pods, track theirs uniqueness based on a custom set of their arguments,
prevent from doubling, and maintain their life-cycle over time.

> _Project named after carousel tug, vessel that helps bigger ships operate in narrow space._

Concept
---

### How it supposed to work

```mermaid
flowchart LR
  subgraph env ["Orchestrated Environment"]
    direction LR
    dm["Service requester"]
    ca["Carousel"]
    dm -- "Request for certain <br /> service configuration" --> ca
    ca -. "Pulling current state" .-> block
    ca -- "Check requested <br /> service instance status" --> ca
    ca -- "Request to pull / up / down" --> block
    ca -- "Return service <br /> connection info" --> dm
    subgraph block [" "]
      direction TB
      i1["Service A instance No 1"]
      i2["Service A instance No 2"]
      in["Service A instance No N"]
      i1 -.- i2 -.- in
    end
  end

  style i2 stroke-width:1px,stroke-dasharray: 1 5
  style in stroke-width:1px,stroke-dasharray: 1 5
```
