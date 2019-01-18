---
id: version-1.0.0-helpers
title: Helpers
original_id: helpers
---
Apenas alguns helpers para utilização como classes.

## Margin

Para aplicar um margin basta utilizar a seguinte sintaxe:

- Margin nos 4 lados: m-"valor"
- Margin top: mt-"valor"
- Margin right: mr-"valor"
- Margin bottom: mb-"valor"
- Margin left: ml-"valor"

>Onde "valor" pode ser um numero **de 1 a 100**;

>Ao adicionar essa classe será aplicado o **"valor" em px** para o tipo de margin utilizado.

### Exemplo Margin
```html
<div class="m-10"> Margin de 10px aplicado aos 4 lados. </div>
<div class="mt-10"> Margin top de 10px. </div>
<div class="mb-10"> Margin bottom de 10px. </div>
<div class="mr-10"> Margin right de 10px. </div>
```

## Padding

Para aplicar um Padding basta utilizar a seguinte sintaxe:

- Padding nos 4 lados: p-"valor"
- Padding top: pt-"valor"
- Padding right: pr-"valor"
- Padding bottom: pb-"valor"
- Padding left: pl-"valor"

>Onde "valor" pode ser um numero **de 1 a 100**;

>Ao adicionar essa classe será aplicado o **"valor" em px** para o tipo de padding utilizado.

### Exemplo Padding
```html
<div class="p-10"> Padding de 10px aplicado aos 4 lados. </div>
<div class="pt-10"> Padding top de 10px. </div>
<div class="pb-10"> Padding bottom de 10px. </div>
<div class="pr-10"> Padding right de 10px. </div>
```

## Width

Para aplicar um Width basta utilizar a seguinte sintaxe:

- Width: w-"valor"

>Onde "valor" pode ser um numero **de 1 a 100**;

>Ao adicionar essa classe será aplicado o **"valor" em %** no width.

### Exemplo Width
```html
<div class="w-10"> Width de 10%. </div>
<div class="w-80"> Width de 80%. </div>
<div class="w-75"> Width de 75%. </div>
```

## Font-Size

Para aplicar um Font-Size basta utilizar a seguinte sintaxe:

- Font-Size: fs-"valor"

>Onde "valor" pode ser um numero **de 1 a 50**;

>Ao adicionar essa classe será aplicado o **"valor" em px** no Font-Size.

### Exemplo Font-Size
```html
<div class="fs-10"> Font-Size de 10px. </div>
<div class="fs-20"> Font-Size de 20px. </div>
<div class="fs-15"> Font-Size de 15px. </div>
```

## Colors

Para aplicar cor nos elementos basta utilizar a seguinte sintaxe:

- class="color-nomedacor"

>Onde **"nomedacor"** pode pode ser preenchido com um dos valores:
> - primary
> - red
> - red-hover
> - yellow
> - yellow-hover

### Exemplo Colors
```html
<div class="color-primary"> Texto com color primary. </div>
<div class="color-red"> Texto com color red. </div>
<div class="color-yellow-hover"> Texto com color yellow hover. </div>
```

## Background Colors

Para aplicar cor nos elementos basta utilizar a seguinte sintaxe:

- class="background-color-nomedacor"

>Onde **"nomedacor"** pode pode ser preenchido com um dos valores:
> - primary
> - red
> - red-hover
> - yellow
> - yellow-hover

### Exemplo Background Colors
```html
<div class="background-color-primary"> Texto com background-color primary. </div>
<div class="background-color-red"> Texto com background-color red. </div>
<div class="background-color-yellow-hover"> Texto com background-color yellow hover. </div>
```