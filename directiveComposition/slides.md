---
layout: cover
---

# Directive composition API
<hr>

<div style="position: absolute; bottom: 20px; right: 20px; display: flex; flex-flow: column; align-items: flex-end">  
    <img src="assets/me.png" class="w-15 h-15 rounded shadow" />
    <div>Stanislav Galiant</div>
    <div style="font-size: 12px">Angular FE developer at <i>Cluepoints</i></div>
</div>

---
layout: center
---

#  How can we combine multiple directives ?

---

# Using Extend 
<hr>

```ts
export class CombinedDirective extends ColorDirective {
    constructor() {
        super();
    }
}
```
<span v-click>
    Pros:
</span>
<ul>
    <li v-click>You can easily override any logic from ColorDirective</li>
</ul>
<span v-click>
    Cons:
</span>
<ul>
    <li v-click>Can only extend one directive</li>
    <li v-click>
        You have to keep track of 'ColorDirective' implementation and dependencies
        <span style="font-size: 10px">(unless you are using inject())</span>
    </li>
</ul>

---

# Using Multiple Directives 
<hr>

```html
<div>
    <span appBold appUnderline appColor>Hover over me</span>
</div>
```
<span v-click>
    Pros:
</span>
<ul>
    <li v-click>User always see what is being applied</li>
    <li v-click>Flexible</li>
</ul>
<span v-click>
    Cons:
</span>
<ul>
    <li v-click>Not really DRY approach</li>
</ul>

--- 

# Using hostDirectives
<hr>

--- 

# Using hostDirectives
<hr>

```ts
    @Directive({
        selector: '[appPainter]',
        standalone: true,
        hostDirectives: [BoldDirective, ColorDirective, UnderlineDirective],
    })
    export class PainterDirective {}
```
<ul>
    <li v-click>Only standalone directives</li>
</ul>

--- 

# Execution order
<hr>
```ts
    @Component({
        selector: 'admin-menu',
        template: 'admin-menu.html',
        hostDirectives: [MenuBehavior],
    })
    export class AdminMenu { }
```
<ul>
    <li v-click>MenuBehavior instantiated</li>
    <li v-click>AdminMenu instantiated</li>
    <li v-click>MenuBehavior receives inputs (ngOnInit)</li>
    <li v-click>AdminMenu receives inputs (ngOnInit)</li>
    <li v-click>MenuBehavior applies host bindings</li>
    <li v-click>AdminMenu applies host bindings</li>
</ul>


---
layout: cover
---

# Thank you







