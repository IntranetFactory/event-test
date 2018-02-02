# event-test

#### Event dispatch method
* HTMLInput.change event
* Polymer.base.fire('change', { ... }, { bubbles: false })
* Polymer.base.fire('change', { ... }, { bubbles: true })
* .dispatchEvent(new Event('change', { ... }, { bubbles: false })
* .dispatchEvent(new Event('change', { ... }, { bubbles: true })
* .dispatchEvent(new Event('change', { ... }, { bubbles: true, composed: true })

#### Does it bubble in v0 ?

| dispatch method | shadyDOM | shadowDOM |
| ------- | -------- | -------- |
| HTMLInput.change event | true | false |
| Polymer.base.fire('change', { ... }, { **bubbles: false** }) | false | false |
| Polymer.base.fire('change', { ... }, { **bubbles: true** }) | true | true |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: false** }) | false | false |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true** }) | true | true |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true, composed: true** }) | true | true |

#### Does it bubble in v1 ?
| dispatch method | shadyDOM | shadowDOM |
| ------- | -------- | -------- |
<<<<<<< HEAD
| HTMLInput.change event | false | false |
| Polymer.base.fire('change', { ... }, { **bubbles: false** }) | false | false |
| Polymer.base.fire('change', { ... }, { **bubbles: true** }) | true | true |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: false** }) | false | false |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true** }) | false | false |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true, composed: true** }) | true | true |
=======
| HTMLInput.change event | | |
| Polymer.base.fire('change', { ... }, { **bubbles: false** }) | | |
| Polymer.base.fire('change', { ... }, { **bubbles: true** }) | | |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: false** }) | | |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true** }) | | |
| .dispatchEvent(new Event('change', { ... }, { **bubbles: true, composed: true** }) | | |
>>>>>>> #v1


