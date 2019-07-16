---
title: 'Instrukcje: Zapoznaj się z omówieniem zestawu schematu przy użyciu widoku wykresu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f6f264427e10cbe444cab8a5208e86866635ed17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150731"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Instrukcje: Omówienie zestawu schematu przy użyciu widoku wykresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [widoku wykresu](../xml-tools/graph-view.md) Aby wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości  
  
1. Utwórz nowy plik schematu XML, a następnie zapisz plik jako Relationships.xsd.  
  
2. Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować podstawowego pliku schematu XML** link widoku startowego.  
  
3. Skopiuj przykładowy kod XML schematu z [schematu XML z próbki: Relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.  
  
4. Kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz pozycję **Projektant widoków**.  
  
5. Wybierz widok wykresu z paska narzędzi XSD.  
  
6. Wybierz **schemat ustawiony** węzła w Eksplorator schematu XML i przeciągnij węzeł projektowania suface widoku wykresu. Powinien zostać wyświetlony wszystkie węzły globalnych i strzałki Łączenie węzłów, które mają relacje.  
  
     ![Widoku wykresu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7. Kliknij dowolny węzeł na powierzchni projektowej i spójrz na pasku nawigacji, aby zobaczyć, gdzie wybrany węzeł znajduje się w zestawie schematów.  
  
8. Rick kliknąć dowolny węzeł elementu na desing powierzchni i wybierz **Generowanie XML przykładowe** można znaleźć w dokumencie wystąpienia XML.
