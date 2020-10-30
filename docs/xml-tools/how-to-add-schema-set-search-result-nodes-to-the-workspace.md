---
title: Dodawanie węzłów wyników wyszukiwania zestawu schematu XML do obszaru roboczego
description: Dowiedz się, jak dodać węzły, które są wyróżnione w Eksploratorze schematu XML jako wynik wyszukiwania słowa kluczowego w obszarze roboczym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e306ec76b6089d822dfdcd154ff1947aef1c9cac
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049177"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego

W tym temacie wyjaśniono, jak dodać węzły, które są wyróżnione w **Eksploratorze schematu XML** jako wynik wyszukiwania słowa kluczowego w obszarze roboczym.

> [!NOTE]
> Do [obszaru roboczego](../xml-tools/xml-schema-designer-workspace.md)można dodawać tylko węzły globalne.

W tym przykładzie zastosowano przykładowy [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Aby dodać węzły wynikowe zestawu schematów

1. Wykonaj kroki opisane w temacie [How to: Create i Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Wpisz "purchaseOrder" w polu tekstowym wyszukiwania na pasku narzędzi [Eksploratora XML](../xml-tools/xml-schema-explorer.md) i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif)

     Wyniki wyszukiwania są wyróżniane w **Eksploratorze schematu XML** i oznaczone przez znaczniki na pionowym pasku przewijania.

3. Dodaj wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyniki podsumowania.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`Węzeł i `PurchaseOrderType` węzeł są wyświetlane obok siebie na powierzchni projektowej [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), zostanie narysowana strzałka między nimi.
