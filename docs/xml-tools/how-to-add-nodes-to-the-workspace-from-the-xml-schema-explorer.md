---
title: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML
description: Dowiedz się, jak dodać węzły do obszaru roboczego projektanta schematu XML z Eksploratora schematu XML za pomocą menu kontekstowego lub przeciągając i upuszczając węzły w widoku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baa4d32d14a85e27bb0bb453c8c81f0bab486379
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045725"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Instrukcje: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML

W tym temacie opisano sposób dodawania węzłów do [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md) z **Eksploratora schematu XML** . Można to osiągnąć przez przeciąganie i upuszczanie węzłów z **Eksploratora schematu XML** do widoku projektanta XSD lub za pomocą menu kontekstowego **Eksploratora schematu XML** . Można również dodać węzły, które są wyróżnione w wyniku wyszukiwania wykonanego przez **Eksploratora schematu XML** . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zestawu schematów wyniki wyszukiwania węzłów do obszaru roboczego](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Tylko węzły globalne można dodać do [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Aby dodać węzły za pomocą menu kontekstowego Eksploratora XML

1. Wykonaj kroki opisane w temacie [How to: Create i Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzeł w EKSPLORATORZE XSD. Wybierz pozycję **Pokaż w widoku wykresu** .

     `purchaseOrderType`Węzeł pojawia się na powierzchni projektowej widoku wykresu.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Aby przeciągnąć i upuścić węzeł w widoku

1. Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzeł w widoku wykresu. Wybierz pozycję **Pokaż w Eksploratorze schematu XML** .

     Węzeł zostanie wyróżniony w **Eksploratorze schematu XML** .

2. Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzeł w **Eksploratorze schematu XML** i wybierz polecenie **Pokaż wszystkie odwołania** .

     `purchaseOrder`Węzeł zostanie wyróżniony.

3. Przeciągnij `purchaseOrder` węzeł do widoku wykresu.

     `purchaseOrder`Węzeł i `PurchaseOrderType` węzeł są wyświetlane obok siebie na powierzchni projektowej widoku wykresu. Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), zostanie narysowana strzałka między nimi.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Aby dodać węzły przy użyciu funkcji wyszukiwania Eksploratora schematu

1. Wpisz "purchaseOrder" w polu tekstowym wyszukiwania na pasku narzędzi [Eksploratora XML](../xml-tools/xml-schema-explorer.md) i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif)

     Wyniki wyszukiwania są wyróżniane w **Eksploratorze schematu XML** i oznaczone przez znaczniki na pionowym pasku przewijania.

2. Dodaj wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyniki podsumowania.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`Węzeł i `PurchaseOrderType` węzeł są wyświetlane obok siebie na powierzchni projektowej [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), zostanie narysowana strzałka między nimi.

## <a name="see-also"></a>Zobacz też

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
