---
title: Sprawdzanie węzłów przy użyciu widoku modelu zawartości w projektancie schematu XML
description: Dowiedz się, jak za pomocą widoku modelu zawartości w projektancie schematu XML sprawdzić model zawartości węzłów w schemacie XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef330e6e189b9cee1126d5de48d55622fe8d9046
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399512"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Instrukcje: Badanie modelu zawartości węzłów przy użyciu widoku modelu zawartości

W tym temacie opisano sposób eksplorowania węzłów przy użyciu [widoku modelu zawartości](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1. Utwórz nowy plik schematu XML.

2. Kliknij pozycję **Użyj edytora XML, aby wyświetlić i edytować źródłowy plik schematu XML** w widoku Start.

3. Skopiuj przykładowy kod schematu XML z [przykładowego schematu XML: schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) i wklej go, aby zastąpić kod, który został domyślnie dodany do nowego pliku XSD.

4. Wybierz `purchaseOrder` element w Eksploratorze schematu, klikając prawym przyciskiem myszy `purchaseOrder` element w edytorze XML i wybierając **Pokaż w Eksploratorze XML**.

5. Kliknij prawym przyciskiem myszy `purchaseOrder` w EKSPLORATORZE XML i wybierz polecenie **Pokaż w widoku modelu zawartości**.

     Widok modelu zawartości wyświetla `purchaseOrder` element na jego powierzchni projektowej.

6. Rozwiń `shipTo` węzły, `billTo` i, `items` dwukrotnie klikając każdy węzeł lub klikając podwójną strzałkę po prawej stronie każdego węzła.

     Węzły `purchaseOrder` elementu są teraz rozwinięte i będzie można zobaczyć model zawartości elementu.

7. Kliknij dowolny węzeł w obszarze `purchaseOrder` elementu i przyjrzyj się na pasku nawigacyjnym, aby zobaczyć, gdzie w zestawie schematu znajduje się wybrany węzeł.

8. Kliknij przycisk **Pokaż dokumentację** na pasku narzędzi XSD, aby przełączyć dokumentację. Możesz również kliknąć prawym przyciskiem myszy powierzchnię projektu, aby przełączać dokumentację.

9. Kliknij prawym przyciskiem myszy `purchaseOrder` węzeł i wybierz polecenie **Generuj przykładowy kod XML** , aby wyświetlić dokument wystąpienia XML.
