---
title: 'Instrukcje: uzyskiwanie przeglądu zestawu schematu przy użyciu widoku wykresu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670897"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Instrukcje: uzyskiwanie przeglądu zestawu schematu przy użyciu widoku wykresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak za pomocą [widoku wykresu](../xml-tools/graph-view.md) wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości

1. Utwórz nowy plik schematu XML i Zapisz plik jako Relationships. xsd.

2. Kliknij przycisk **Użyj edytora XML, aby wyświetlić i edytować źródłowy plik schematu XML** w widoku Start.

3. Skopiuj przykładowy kod schematu XML z [przykładowego schematu XML: relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go, aby zastąpić kod, który został domyślnie dodany do nowego pliku XSD.

4. Kliknij prawym przyciskiem myszy w dowolnym miejscu edytora XML i wybierz polecenie **Projektant widoków**.

5. Wybierz widok wykresu z poziomu paska narzędzi XSD.

6. Wybierz węzeł **zestaw schematów** w EKSPLORATORZE schematu XML i przeciągnij węzeł do projektu suface widoku wykresu. Powinny być widoczne wszystkie węzły globalne i strzałki łączące węzły z relacjami.

     ![Widok wykresu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Kliknij dowolny węzeł na powierzchni projektowej i spójrz na pasek nawigacyjny, aby zobaczyć, gdzie wybrany węzeł znajduje się w zestawie schematów.

8. Rick — kliknij dowolny węzeł elementu na wyznaczonej powierzchni i wybierz polecenie **Generuj przykładowy kod XML** , aby wyświetlić dokument wystąpienia XML.
