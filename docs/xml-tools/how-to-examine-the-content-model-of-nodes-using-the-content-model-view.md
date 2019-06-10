---
title: Sprawdź węzłów przy użyciu widoku modelu zawartości w Projektancie schematu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63e337162dc8499bf9ac2acb5606fbf75292574f
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820463"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Instrukcje: Badanie modelu zawartości węzłów przy użyciu widoku modelu zawartości

W tym temacie opisano sposób zapoznaj się z węzłów za pomocą [widoku modelu zawartości](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1. Utwórz nowy plik schematu XML.

2. Kliknij przycisk **edytora XML użyj do wyświetlania i edytowania pliku schematu XML podstawowego** w widoku startowego.

3. Skopiuj przykładowy kod XML schematu z [schematu XML przykładowych: schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.

4. Wybierz `purchaseOrder` element w Eksploratorze schematu, klikając prawym przyciskiem myszy `purchaseOrder` elementu w pliku XML edytora i zaznaczanie **Pokaż w Eksploratorze XML**.

5. Kliknij prawym przyciskiem myszy `purchaseOrder` w Eksploratorze XML, a następnie wybierz pozycję **Pokaż w widoku modelu zawartości**.

     Wyświetla widok modelu zawartości `purchaseOrder` elementu po jego powierzchni projektowej.

6. Rozwiń `shipTo`, `billTo`, i `items` węzłów przez dwukrotne kliknięcie każdego węzła lub klikając podwójną strzałkę z prawej strony każdego węzła.

     Węzły `purchaseOrder` element teraz zostaną rozwinięte i można zobaczyć model zawartości elementu.

7. Kliknij w dowolnym węźle `purchaseOrder` elementu i spójrz na pasku nawigacji, aby zobaczyć, gdzie w zestawie schematów wybrany węzeł znajduje się.

8. Kliknij przycisk **Pokaż dokumentacji** przycisk na pasku narzędzi XSD, aby przełączyć dokumentacji. Możesz również prawym przyciskiem myszy powierzchnię projektu, aby przełączyć się z dokumentacją.

9. Kliknij prawym przyciskiem myszy `purchaseOrder` a następnie wybierz węzeł **Generowanie XML przykładowe** można znaleźć w dokumencie wystąpienia XML.
