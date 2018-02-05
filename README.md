# event-test

#### Event dispatch method
* HTMLInput.change event
* Polymer.base.fire('change', { ... }, { bubbles: false })
* Polymer.base.fire('change', { ... }, { bubbles: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: false })
* .dispatchEvent(new CustomEvent('change', { bubbles: false, composed: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: true })
* .dispatchEvent(new CustomEvent('change', { bubbles: true, composed: true })

### Change event

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
|                                                                 | Chrome  | true<sup>1</sup> / true<sup>1</sup> | false / **false** |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true** }) | Firefox | true<sup>1</sup> / NA | false / NA |
|                                                                 | Edge    | true<sup>1</sup> / NA | false / NA |
|                                                                                 | Chrome  | true / true | true / true |
| .dispatchEvent(new CustomEvent('change', { **bubbles: true, composed: true** }) | Firefox | true / NA | true / NA |
|                                                                                 | Edge    | true / NA | true / NA |

<sup>1</sup> Event bubbles from event-source only, it doesn't bubble form event-source-lv2 and event-source-lv3


### Click event

#### What happens in ShadowDOM v0 ?
|  |  | Bubbling ? |  | Listeners called |  |
|  ------ | ------ | :------: | ------ | :------: | ------ |
| Dispatch Method | Browser | shadyDOM | shadowDOM | shadyDOM | shadowDOM |
|                        | Chrome | true | true | true | true |
| HTMLInput.click event | Firefox | true | N/A | true | N/A |
|                        | Edge | true | N/A | true | N/A |
|                                                          | Chrome | false | false | false | **true** |
| Polymer.base.fire('click', { }, { **bubbles: false** })  | Firefox | false | N/A | false | N/A |
|                                                          | Edge | false | N/A | false | N/A |
|                                                        | Chrome | true | true | true | true |
| Polymer.base.fire('click', { }, { **bubbles: true** }) | Firefox | true | N/A | true | N/A |
|                                                        | Edge | true | N/A | true | N/A |
|                                                                 | Chrome | false | false | false | **true** |
| .dispatchEvent(new CustomEvent('click', { **bubbles: false** }) | Firefox | false | N/A | false | N/A |
|                                                                 | Edge | false | N/A | false | N/A |
|                                                                                  | Chrome | false | false | false | **true** |
| .dispatchEvent(new CustomEvent('click', { **bubbles: false, composed: true** }) | Firefox | false | N/A | false | N/A |
|                                                                                  | Edge | false | N/A | false | N/A |
|                                                                | Chrome | true | true | true | true |
| .dispatchEvent(new CustomEvent('click', { **bubbles: true** }) | Firefox | true | N/A | true | N/A |
|                                                                | Edge | true | N/A | true | N/A |
|                                                                                | Chrome | true | true | true | true |
| .dispatchEvent(new CustomEvent('click', { **bubbles: true, composed: true** }) | Firefox | true | N/A | true | N/A |
|                                                                                | Edge | true | N/A | true | N/A |

#### What happens in ShadowDOM v1 ?

|   |  | Bubbling ? |  | Listeners called |  |
|  ------ | ------ | :------: | ------ | :------: | ------ |
|  Dispatch Method | Browser | shadyDOM | shadowDOM | shadyDOM | shadowDOM |
|                       | Chrome | true | true | true | true |
| HTMLInput.click event | Firefox | true | N/A | true | N/A |
|                       | Edge | true | N/A | true | N/A |
|                                                         | Chrome | false | **false** | true | **true** |
| Polymer.base.fire('click', { }, { **bubbles: false** }) | Firefox | false | N/A | false | N/A |
|                                                         | Edge | false | N/A | false | N/A |
|                                                        | Chrome | true | true | true | true |
| Polymer.base.fire('click', { }, { **bubbles: true** }) | Firefox | true | N/A | true | N/A |
|                                                        | Edge | true | N/A | true | N/A |
|                                                                 | Chrome | false | false | false | false |
| .dispatchEvent(new CustomEvent('click', { **bubbles: false** }) | Firefox | false | N/A | false | N/A |
|                                                                 | Edge | false | N/A | false | N/A |
|                                                                                 | Chrome | false | **false** | true | **true** |
| .dispatchEvent(new CustomEvent('click', { **bubbles: false, composed: true** }) | Firefox | false | N/A | false | N/A |
|                                                                                 | Edge | false | N/A | false | N/A |
|                                                                | Chrome | TRUE¹ | TRUE¹ | false | false |
| .dispatchEvent(new CustomEvent('click', { **bubbles: true** }) | Firefox | TRUE¹ | N/A | false | N/A |
|                                                                | Edge | TRUE¹ | N/A | false | N/A |
|                                                                                | Chrome | true | true | true | true |
| .dispatchEvent(new CustomEvent('click', { **bubbles: true, composed: true** }) | Firefox | true | N/A | true | N/A |
|                                                                                | Edge | true | N/A | true | N/A |

<sup>1</sup>click event bubbles only for event-source (depth 1). For event-source-lv2 and event-source-lv3 click event doesn't bubble
