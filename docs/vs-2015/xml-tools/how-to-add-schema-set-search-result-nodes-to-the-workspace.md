---
title: 'Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666548"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wyjaśniono, jak dodać węzły, które są wyróżnione w Eksploratorze schematu XML jako wynik wyszukiwania słowa kluczowego w obszarze roboczym.

> [!NOTE]
> Do [obszaru roboczego](../xml-tools/xml-schema-designer-workspace.md)można dodawać tylko węzły globalne.

 W tym przykładzie zastosowano przykładowy [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md).

### <a name="to-add-schema-set-result-nodes"></a>Aby dodać węzły wynikowe zestawu schematów

1. Wykonaj kroki opisane w temacie [How to: Create i Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Wpisz "purchaseOrder" w polu tekstowym wyszukiwania na pasku narzędzi [Eksploratora XML](../xml-tools/xml-schema-explorer.md) i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Wyniki wyszukiwania są wyróżniane w Eksploratorze schematu XML i oznaczone przez znaczniki na pionowym pasku przewijania.

3. Dodaj wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyniki podsumowania.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder`Węzeł i `PurchaseOrderType` węzeł są wyświetlane obok siebie na powierzchni projektowej [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), zostanie narysowana strzałka między nimi.
