# event-test

#### Event dispatch method
* HTMLInput.change event
* Polymer.base.fire('change', { ... }, { bubbles: false })
* Polymer.base.fire('change', { ... }, { bubbles: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: false })
* .dispatchEvent(new CustomEvent('change', { bubbles: false, composed: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: true, composed: true })

#### What happens in shadowDOM v0 ?

| dispatch method | Browser | bubbling shady/shadow | listeners called shady/shadow |
| ------- | -------- | -------- | -------- |
|                        | Chrome  | true / false | true / false |
| HTMLInput.change event | Firefox | true / NA    | true / NA |
|                        | Edge    | true / NA    | true / NA |
|                                                          | Chrome  | false / **false** | false / **true** |
| Polymer.base.fire('change', { }, { **bubbles: false** }) | Firefox | false / NA    | false / NA |
|                                                          | Edge    | false / NA    | false / NA |
|                                                         | Chrome  | true / true | true / true |
| Polymer.base.fire('change', { }, { **bubbles: true** }) | Firefox | true / NA | true / NA |
|                                                         | Edge    | true / NA | true / NA |
|                                                                  | Chrome  | false / **false** | false / **true** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: false** }) | Firefox | false / NA | false / NA |
|                                                                  | Edge    | false / NA | false / NA |
|                                                                                  | Chrome  | false / **false** | false / **true** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: false, composed: true** }) | Firefox | false / NA | false / NA |
|                                                                                  | Edge    | false / NA | false / NA |
|                                                                 | Chrome  | true / true | true / true |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true** }) | Firefox | true / NA | true / NA |
|                                                                 | Edge    | true / NA | true / NA |
|                                                                                 | Chrome  | true / true | true / true |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true, composed: true** }) | Firefox | true / NA | true / NA |
|                                                                                 | Edge    | true / NA | true / NA |


#### Does it bubble in v0 ?

| dispatch method | Chrome | Firefox | Edge |
| ------- | -------- | -------- | -------- |
| | shady (shadow) | shady (shadow) | shady (shadow) |
| HTMLInput.change event | true | false | |
|  | false | false | |
| Polymer.base.fire('change', { ... }, { **bubbles: true** }) | true | true | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: false** }) | false | false | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: true** }) | true | true | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: true, composed: true** }) | true | true | |

#### Does it bubble in v1 ?
| dispatch method | shadyDOM | shadowDOM |
| ------- | -------- | -------- |
| HTMLInput.change event | | |
| Polymer.base.fire('change', { ... }, { **bubbles: false** }) | | |
| Polymer.base.fire('change', { ... }, { **bubbles: true** }) | | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: false** }) | | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: true** }) | | |
| .dispatchEvent(new CustomEvent('change', { ... }, { **bubbles: true, composed: true** }) | | |


