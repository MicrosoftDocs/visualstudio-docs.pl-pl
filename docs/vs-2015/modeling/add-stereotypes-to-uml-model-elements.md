---
title: Dodawanie stereotypów do elementów modelu UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bba638a595a01f17e4b7e4f8269a69cb6e466a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430491"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Dodawanie stereotypów do elementów modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dodać stereotyp modelu UML, aby dodać adnotacje ją i udostępniać specjalne właściwości. Aby dodać stereotyp do elementu modelu, stereotyp musi być zdefiniowana w profilu, a do pakietu lub modelu, który zawiera element modelu, należy połączyć profil. Każdy stereotyp można dodawać tylko dla niektórych rodzajów elementu modelu, takich jak klasy UML, przypadki użycia lub składniki.  
  
 Na przykład jeśli chcesz zdefiniować klasy UML z stereotyp «specyfikacji», należy go utworzyć w ramach pakietu lub modelu, który jest połączony z standardowa L2 profilu.  
  
 Domyślnie każdy model jest przez połączone standardowa L2 profilów UML i L3.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Aby połączyć profil modelu lub pakietu  
  
1. Otwórz **Eksploratora modelu UML**. Na **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
2. Zlokalizuj pakiet lub model, który zawiera wszystkie elementy, dla których chcesz zastosować stereotypy w profilu.  
  
3. Kliknij prawym przyciskiem myszy pakiet lub model, a następnie kliknij przycisk **właściwości**.  
  
4. W **właściwości** oknie **profile** właściwość profile, które zawierają stereotypów, którego chcesz użyć.  
  
     Stereotypy profilu będą teraz dostępne w przypadku wszystkich elementów w modelu lub pakietu. Jeśli pakiet zawiera inne pakiety, stereotypy będzie również dostępna w przypadku elementów wewnątrz nich.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Dodawanie stereotypów do elementów modelu lub relacji  
  
1. Kliknij prawym przyciskiem myszy element modelu lub relacji, na diagramie lub w **Eksploratora modelu UML**, a następnie kliknij przycisk **właściwości**.  
  
    > [!NOTE]
    > Aby dodać ten sam Stereotypy do kilku elementów, można wybrać wiele elementów i kliknij prawym przyciskiem myszy jeden z nich.  
  
2. Kliknij przycisk **Stereotypy** właściwości i wybierz pozycję stereotypów, które chcesz zastosować.  
  
     Wybrane Stereotypy pojawiają się ostrokątnego «» w element modelu, w przypadku większości elementów i relacji.  
  
    > [!NOTE]
    > Jeśli nie widzisz **Stereotypy** właściwości, lub jeśli nie ma stereotyp ma, upewnij się, że element modelu znajduje się wewnątrz pakietu lub modelu, do którego został połączony odpowiedni profil.  
  
3. Niektóre Stereotypy umożliwiają ustawienie wartości dodatkowe właściwości dla elementu modelu. Aby wyświetlić te właściwości, rozwiń węzeł **Stereotypy** właściwości.  
  
### <a name="to-create-model-elements-within-a-package"></a>Do tworzenia elementów modelu w ramach pakietu  
  
1. Utwórz pakiet diagramu klas UML, albo w **Eksploratora modelu UML**.  
  
2. Dodaj elementy modelu do pakietu w jednym z następujących sposobów:  
  
    - Na diagramie klas UML kliknij narzędzie do elementu, a następnie kliknij wewnątrz pakietu na diagramie.  
  
         \- lub —  
  
    - W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy pakiet, wskaż opcję **Dodaj**, a następnie kliknij typ elementu.  
  
         \- lub —  
  
    - W Eksploratorze modelu UML przeciągnij istniejącego elementu do pakietu.  
  
         \- lub —  
  
    - Łączenie diagramu do pakietu, a następnie utwórz elementy na diagramie.  
  
         Aby to zrobić, kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij przycisk **właściwości**. W **właściwości** oknie **połączone pakietu** do żądanego pakietu.  
  
         Wszystkie nowe elementy, które tworzysz na diagramie są definiowane w tym pakiecie.  
  
         Można w tym tylko w przypadku niektórych rodzajów diagramu.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md)   
 [Kolor klas UML przez stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)
