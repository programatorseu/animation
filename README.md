# Animation

```html
<div class="pulser"></div>
```

```css
/* Decorative styles */
body {
  display: grid;
  place-items: center;
}

.pulser {
  width: 30px;
  height: 30px;
  background: rebeccapurple;
  border-radius: 50%;
  position: relative;
}


.pulser::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: blueviolet;
  border-radius: 50%;
  z-index: -1;
}

.pulser::after {
  animation: pulse 1000ms cubic-bezier(0.9, 0.7, 0.5, 0.9) infinite;
}

@keyframes pulse {
  0% {
    opacity: 0;
  }
  50% {
    transform: scale(1.4);
    opacity: 0.4;
  }
}



```

animation can be simple (one state) or complex (time-based)



### Keyframe

mechanism we can use to assign **animation** states to **timestamps**, along a **timeline**.

above pulser  - The entire animation runs for 1 second and runs over 2 states.

![image-20220706132931426](/home/programators/.var/app/io.typora.Typora/config/Typora/typora-user-images/image-20220706132931426.png)

**@keyframes**

basic 2 states   (from (0%) - to (100%))

```css
@keyframes our-name {
    from {
        
    }
    to {
        
    }
}
```



**animation properties**

- animation-duration
- animation-timing-function

```css
.my-element {
	animation-duration: 10s;
}
```

```html
<div class="grower"></div>
```

```css
.grower {
  width:200px;
  height:80px;
  background:lightseagreen;
  position:relative;
  margin:auto;
  animation-name:grow;
  animation-duration:2s;
  animation-iteration-count:infinite;
  animation-timing-function:linear;
}

@keyframes grow {
  0% {
    transform:scaleX(1);
  }
  50% {
    transform:scaleX(1.8);
    background:darkgreen;
  }
}

```

https://cubic-bezier.com/#.17,.67,.83,.67



**steps easing function**

if we want to move in intervals 

- 1st argument (how many steps )
- 2nd argument - direction

```html
<div class="steps">
</div>
```



```css
.steps {
  width:50px;
  height:20px;
  background:royalblue;
  animation:move;
  animation-duration:2s;
  animation-iteration-count:infinite;
  animation-timing-function:steps(5,end);
}

@keyframes move {
  from {
    transform:translateX(0px);
  }
  to {
    transform:translateX(300px);
  }
}

```

The [animation-iteration-count](https://developer.mozilla.org/docs/Web/CSS/animation-iteration-count) property defines how many times the `@keyframes` timeline should run. By default, this is 1, 

`animation-direction`

`normal`: the default value, which is forwards.

`reverse`: runs backwards over your timeline.

`alternate`: for each animation iteration, the timeline will run forwards or backwards in sequence.

`animation-delay`  -> how long wait before starting animation





**animation-play-state**

 allows  to play and pause the animation. 

```css
.grower:hover {
  animation-play-state: paused;
  cursor: wait;
}
```

**animation-fill-mode**

defines which values in `@keyframes` persist before animation start or after it ends 

`forwards`: The last keyframe will persist, based on the animation direction.

`backwards`: The first keyframe will persist, based on the animation direction.



**animation shorthand**

1. `animation-name`
2. `animation-duration`
3. `animation-timing-function`
4. `animation-delay`
5. `animation-iteration-count`
6. `animation-direction`
7. `animation-fill-mode`
8. `animation-play-state`



```css
.my-element {
	animation: my-animation 10s ease-in-out 1s infinite forwards forwards running;
}
```



Users can define in their operating system that they prefer to reduce  motion experienced when they interact with applications and websites.  This preference can be detected using the [prefers-reduced-motion](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-reduced-motion) media query.



```css
@media (prefers-reduced-motion) {
  .my-autoplaying-animation {
    animation-play-state: paused;
  }
}
```

