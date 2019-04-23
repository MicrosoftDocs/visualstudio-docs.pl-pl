---
title: 'Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2f14fb52294fc06340f0e179a324d21ec3ecbbb5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116826"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób dodawania węzłów, które są wyróżnione w Eksplorator schematu XML jako wynik wyszukiwania słów kluczowych, w obszarze roboczym.  
  
> [!NOTE]
>  Tylko globalne węzły mogą być dodawane do [obszaru roboczego](../xml-tools/xml-schema-designer-workspace.md).  
  
 W tym przykładzie użyto przykładu [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Aby dodać węzłów wyników zestawu schematu  
  
1. Postępuj zgodnie z instrukcjami w [jak: Tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. W polu tekstowym wyszukiwania wpisz "purchaseOrder" [Eksplorator XML](../xml-tools/xml-schema-explorer.md) paska narzędzi i kliknij przycisk wyszukiwania.  
  
     ![XML Schema Explorer Keyword Search](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Wyniki wyszukiwania są wyróżnione Eksploratora schematu XML i oznaczone przez znaczniki na pionowy pasek przewijania.  
  
3. Dodaj wyniki wyszukiwania do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.  
  
     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Węzła i `PurchaseOrderType` węzła wyświetlane obok siebie na powierzchni projektowania [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowana między nimi.
