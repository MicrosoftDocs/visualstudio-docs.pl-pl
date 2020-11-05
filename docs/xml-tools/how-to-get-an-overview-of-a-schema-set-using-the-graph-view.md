---
title: 'Projektant schematu XML: pobieranie zestawu schematów — Omówienie przy użyciu widoku wykresu'
description: Dowiedz się, jak używać widoku grafu w Eksploratorze schematu XML, aby wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 553b9f2d84f70c75ebcee40cdffe044237c23a5f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398491"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Instrukcje: uzyskiwanie przeglądu zestawu schematu przy użyciu widoku wykresu

W tym temacie opisano, jak za pomocą [widoku wykresu](../xml-tools/graph-view.md) wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1. Utwórz nowy plik schematu XML i Zapisz plik jako *Relationships. xsd*.

2. Kliknij przycisk **Użyj edytora XML, aby wyświetlić i edytować źródłowy plik schematu XML** w widoku Start.

3. Skopiuj przykładowy kod schematu XML z [przykładowego schematu XML: relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go, aby zastąpić kod, który został domyślnie dodany do nowego pliku XSD.

4. Kliknij prawym przyciskiem myszy w dowolnym miejscu edytora XML i wybierz polecenie **Projektant widoków**.

5. Wybierz widok wykresu z poziomu **paska narzędzi XSD**.

6. Wybierz węzeł **zestaw schematów** w **Eksploratorze schematu XML** i przeciągnij węzeł na powierzchnię projektu widoku wykresu. Powinny być widoczne wszystkie węzły globalne i strzałki łączące węzły z relacjami.

     ![Widok wykresu](../xml-tools/media/relationshipingraphview.gif)

7. Kliknij dowolny węzeł na powierzchni projektowej i spójrz na pasek nawigacyjny, aby zobaczyć, gdzie wybrany węzeł znajduje się w zestawie schematów.

8. Rick — kliknij dowolny węzeł elementu na powierzchni projektowej i wybierz polecenie **Generuj przykładowy kod XML** , aby wyświetlić dokument wystąpienia XML.
