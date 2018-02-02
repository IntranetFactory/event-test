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

#### What happens in shadowDOM v1 ?

| dispatch method | Browser | bubbling shady/shadow | listeners called shady/shadow |
| ------- | -------- | -------- | -------- |
|                        | Chrome  | false / false | false / false |
| HTMLInput.change event | Firefox | false / NA    | false / NA |
|                        | Edge    | false / NA    | false / NA |
|                                                          | Chrome  | **false** / **false** | **true** / **true** |
| Polymer.base.fire('change', { }, { **bubbles: false** }) | Firefox | false / NA    | false / NA |
|                                                          | Edge    | false / NA    | false / NA |
|                                                         | Chrome  | true / true | true / true |
| Polymer.base.fire('change', { }, { **bubbles: true** }) | Firefox | true / NA | true / NA |
|                                                         | Edge    | true / NA | true / NA |
|                                                                  | Chrome  | false / **false** | false / **false** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: false** }) | Firefox | false / NA | false / NA |
|                                                                  | Edge    | false / NA | false / NA |
|                                                                                  | Chrome  | **false** / **false** | **true** / **true** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: false, composed: true** }) | Firefox | false / NA | false / NA |
|                                                                                  | Edge    | false / NA | false / NA |
|                                                                 | Chrome  | true<sup>1</sup> / true<sup>1</sup> | true / **false** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true** }) | Firefox | true<sup>1</sup> / NA | true / NA |
|                                                                 | Edge    | true<sup>1</sup> / NA | true / NA |
|                                                                                 | Chrome  | true / true | true / true |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true, composed: true** }) | Firefox | true / NA | true / NA |
|                                                                                 | Edge    | true / NA | true / NA |

<sup>1</sup> Event bubbles from event-source only, it doesn't bubble form event-source-lv2 and event-source-lv3
