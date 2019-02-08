---
title: 'Instrukcje: Omówienie zestawu schematu przy użyciu widoku wykresu w schemacie XML projektanta'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 603761f2886ffc64170774a2d6c460d39596454b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922033"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Instrukcje: Zapoznaj się z omówieniem schematu z zestawu przy użyciu widoku wykresu

W tym temacie opisano sposób użycia [widoku wykresu](../xml-tools/graph-view.md) Aby wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1.  Utwórz nowy plik schematu XML, a następnie zapisz plik jako *Relationships.xsd*.

2.  Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować podstawowego pliku schematu XML** link widoku startowego.

3.  Skopiuj przykładowy kod XML schematu z [schematu XML przykładowych: relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.

4.  Kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz pozycję **Projektant widoków**.

5.  Wybierz widok wykresu z **narzędzi XSD**.

6.  Wybierz **schemat ustawiony** w węźle **Eksploratora schematu XML** i przeciągnij węzeł na powierzchni projektowej widoku wykresu. Powinien zostać wyświetlony wszystkie węzły globalnych i strzałki Łączenie węzłów, które mają relacje.

     ![Widok wykresu](../xml-tools/media/relationshipingraphview.gif)

7.  Kliknij dowolny węzeł na powierzchni projektowej i spójrz na pasku nawigacji, aby zobaczyć, gdzie wybrany węzeł znajduje się w zestawie schematów.

8.  Rick kliknąć dowolny węzeł elementu na projekt powierzchni i wybierz **Generowanie XML przykładowe** można znaleźć w dokumencie wystąpienia XML.