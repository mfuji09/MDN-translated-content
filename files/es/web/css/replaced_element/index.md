---
title: Elemento de reemplazo
slug: Web/CSS/Replaced_element
tags:
  - CSS
  - CSS Referência
  - Intermediate
translation_of: Web/CSS/Replaced_element
original_slug: Web/CSS/Elemento_reemplazo
---
{{CSSRef()}}

## Summary

Dentro de CSS tenemos los **elementos de reemplazo**, cuya representacion esta fuera del ambito de propio CSS. Son un tipo de objeto externo, por tanto su representacion es independiente de CSS. Algunos objetos que normalmente funcionan como objetos de reemplazo son {{HTMLElement("img")}}, {{HTMLElement("object")}}, {{HTMLElement("video")}} o elementos de formulario como {{HTMLElement("textarea")}}, {{HTMLElement("input")}}. Algunos elementos como {{HTMLElement("audio")}} or {{HTMLElement("canvas")}} ejercen como elementos de reemplazo solo en casos especificos. Los objetos insertados a traves de las propiedades CSS {{cssxref("content")}} son _objetos de reemplazo anonimos._.

CSS gestiona elementos de reemplazo en casos concretos, por ejemplo al calcular los margenes y algunos `auto` valores.

Recuerda que algunos elementos de reemplazo, no todos, tienen dimensiones intrinsecas o linea de base establecida, las cuales son utilizadas por propiedades de CSS como {{cssxref("vertical-align")}}.

## Ver tambien:

- {{CSS_key_concepts()}}
