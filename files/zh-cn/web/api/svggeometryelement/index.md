---
title: SVGGeometryElement
slug: Web/API/SVGGeometryElement
tags:
  - API
  - DOM
  - NeedsExample
  - NeedsTranslation
  - Reference
  - SVG
  - SVG DOM
  - TopicStub
translation_of: Web/API/SVGGeometryElement
---
{{APIRef("SVG")}}

The `SVGGeometryElement` interface represents SVG elements whose rendering is defined by geometry with an equivalent path, and which can be filled and stroked. This includes paths and the basic shapes.

{{InheritanceDiagram(600, 140)}}

> **备注：** The `pathLength` property and the `getTotalLength()` and `getPointAtLength()` methods were originally part of the {{domxref("SVGPathElement")}} interface. In SVG 2 they were moved to this interface.

## Properties

_This interface also inherits properties from its parent, {{domxref("SVGGraphicsElement")}}._

- {{domxref("SVGGeometryElement.pathLength")}} {{readOnlyInline}}
  - : This property reflects the {{SVGAttr("pathLength")}} attribute.

## Methods

_This interface also inherits methods from its parent, {{domxref("SVGGraphicsElement")}}._

- {{domxref("SVGGeometryElement.isPointInFill()")}}
  - : Determines whether a given point is within the fill shape of an element. Normal hit testing rules apply; the value of the {{cssxref("pointer-events")}} property on the element determines whether a point is considered to be within the fill.
- {{domxref("SVGGeometryElement.isPointInStroke()")}}
  - : Determines whether a given point is within the stroke shape of an element. Normal hit testing rules apply; the value of the {{cssxref("pointer-events")}} property on the element determines whether a point is considered to be within the stroke.
- {{domxref("SVGGeometryElement.getTotalLength()")}}
  - : Returns the user agent's computed value for the total length of the path in user units.
- {{domxref("SVGGeometryElement.getPointAtLength()")}}
  - : Returns the point at a given distance along the path.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat("api.SVGGeometryElement")}}
