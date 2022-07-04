# Css motion

## 1. Css Transitions

### 1.1 css transition - rolling a ball

**transition** - describes how property should display change when given a different value 

not all is transitionable !:)

**duration** in seconds or miliseconds 

>  JS parses miliseconds
>
> most of things run in miliseconds 

**timing** - optional / deafault is ease

**delay** - optional / number of ms to delay transition before firing it  | deafault is 0

```css
transition: color 2s 100ms; /*property, duration, delay*/
```

```html
<div class="ball"></div>
<img class="paw" src="https://s3.amazonaws.com/stash.rachelnabors.com/codepen/css-animation-workshop/paw.png" />
```

```css
.paw {
  transition: transform .25s ease-in;
}

.playing .paw {
  transform: translateX(30px);
}
.paw {
  position: absolute; top: 0; left: 80px;
}
.ball {
  background: #0097C0;
  border-radius: 50%;
  position: absolute; top: 200px; left: 160px;
  width: 100px; height: 100px;
}

body { background: #e3edf2; }

/* CP_DoFullRefresh */
```

jquery - load event :

```js
$(window).load(function(){
  $("body").addClass("playing");
});
```



then to move ball with delay

```css
.ball {
  transition:transform 1s .25s;
}
.playing .ball { transform:translateX(235px);
}
```

### 1.2 multiple props -  changing ball' color

```css
transition-property:all
```

do not do it ! :) - try to optimize 

```css
.ball {
  transition:
    background .9s .65s
    transform: .4s .25s;
}
```

### 1.3. Duration

3 timeframes for user attention

- instantenous : 100ms
- 1s - we are still connected
- 10s - disconnected

250~300ms - sweet spot : ) 



### 1.4 Timing functions - physics to the ball 

**easing**

- descirbes an animation's rate of change over time 

ease-in (slow-in)

esase-out(slow-out)

cubic-bezier

