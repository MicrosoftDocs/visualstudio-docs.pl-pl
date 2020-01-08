---
title: Sprawdzanie węzłów przy użyciu widoku modelu zawartości w projektancie schematu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592714"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Instrukcje: Badanie modelu zawartości węzłów przy użyciu widoku modelu zawartości

W tym temacie opisano sposób eksplorowania węzłów przy użyciu [widoku modelu zawartości](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1. Utwórz nowy plik schematu XML.

2. Kliknij pozycję **Użyj edytora XML, aby wyświetlić i edytować źródłowy plik schematu XML** w widoku Start.

3. Skopiuj przykładowy kod schematu XML z [przykładowego schematu XML: schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) i wklej go, aby zastąpić kod, który został domyślnie dodany do nowego pliku XSD.

4. Wybierz element `purchaseOrder` w Eksploratorze schematu, klikając prawym przyciskiem myszy element `purchaseOrder` w edytorze XML i wybierając pozycję **Pokaż w EKSPLORATORZE XML**.

5. Kliknij prawym przyciskiem myszy `purchaseOrder` w Eksploratorze XML i wybierz polecenie **Pokaż w widoku modelu zawartości**.

     Widok modelu zawartości wyświetla element `purchaseOrder` na jego powierzchni projektowej.

6. Rozwiń węzły `shipTo`, `billTo`i `items` przez dwukrotne kliknięcie każdego węzła lub kliknięcie podwójnej strzałki z prawej strony każdego węzła.

     Węzły elementu `purchaseOrder` są teraz rozwinięte i można zobaczyć model zawartości elementu.

7. Kliknij dowolny węzeł w obszarze `purchaseOrder` i spójrz na pasek nawigacyjny, aby zobaczyć, gdzie w zestawie schematu znajduje się wybrany węzeł.

8. Kliknij przycisk **Pokaż dokumentację** na pasku narzędzi XSD, aby przełączyć dokumentację. Możesz również kliknąć prawym przyciskiem myszy powierzchnię projektu, aby przełączać dokumentację.

9. Kliknij prawym przyciskiem myszy węzeł `purchaseOrder` i wybierz polecenie **Generuj przykładowy kod XML** , aby wyświetlić dokument wystąpienia XML.
