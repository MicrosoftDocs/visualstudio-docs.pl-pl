---
title: Dodaj stereotypy do elementów modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74292333"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Dodawanie stereotypów do elementów modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dodać stereotyp do elementu modelu UML, aby dodawać do niego adnotacje i udostępniać je wyspecjalizowanym właściwościom. Aby dodać stereotyp do elementu modelu, stereotyp musi być zdefiniowany w profilu i należy połączyć profil z pakietem lub z modelem zawierającym element modelu. Każdy stereotyp można dodać tylko do określonych rodzajów elementu modelu, takich jak klasy UML, przypadki użycia lub składniki.

 Na przykład jeśli chcesz zdefiniować klasę UML z stereotypem «Specyfikacja», musisz ją utworzyć w pakiecie lub modelu połączonym z profilem standardowym L2.

 Domyślnie każdy model jest połączony z profilami standardowymi UML i L3.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Aby połączyć profil z modelem lub pakietem

1. Otwórz **Eksploratora modelu UML**. W menu **Architektura** wskaż polecenie **Windows**, a następnie kliknij pozycję **Eksplorator modelu UML**.

2. Znajdź pakiet lub model, który zawiera wszystkie elementy, do których chcesz zastosować stereotypy w profilu.

3. Kliknij prawym przyciskiem myszy pakiet lub model, a następnie kliknij polecenie **Właściwości**.

4. W oknie **Właściwości** ustaw właściwość **Profile** na profile zawierające stereotypy, których chcesz użyć.

     Stereotypy profilu będą teraz dostępne dla wszystkich elementów wewnątrz modelu lub pakietu. Jeśli pakiet zawiera inne pakiety, stereotypy będą również dostępne dla elementów wewnątrz nich.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Aby dodać stereotypy do elementów modelu lub relacji

1. Kliknij prawym przyciskiem myszy element modelu lub relację, na diagramie lub w **Eksploratorze modelu UML**, a następnie kliknij polecenie **Właściwości**.

    > [!NOTE]
    > Aby dodać te same stereotypy do kilku elementów, można wybrać kilka elementów, a następnie kliknąć prawym przyciskiem myszy jeden z nich.

2. Kliknij właściwość **stereotypy** i wybierz stereotypy, które chcesz zastosować.

     Wybrane Stereotypy pojawiają się w obrębie elementu "pagons" w elemencie modelu, dla większości rodzajów elementów i relacji.

    > [!NOTE]
    > Jeśli nie widzisz właściwości **stereotypów** lub jeśli odpowiedni stereotyp nie jest wyświetlany, sprawdź, czy element modelu znajduje się w pakiecie lub modelu, do którego został połączony odpowiedni profil.

3. Niektóre stereotypy umożliwiają ustawienie wartości dodatkowych właściwości dla elementu modelu. Aby wyświetlić te właściwości, rozwiń Właściwość **stereotypy** .

### <a name="to-create-model-elements-within-a-package"></a>Aby utworzyć elementy modelu w ramach pakietu

1. Utwórz pakiet w diagramie klas UML lub w **Eksploratorze modelu UML**.

2. Dodaj elementy modelu do pakietu w jeden z następujących sposobów:

    - Na diagramie klasy UML kliknij narzędzie dla elementu, a następnie kliknij wewnątrz pakietu na diagramie.

         \- oraz

    - W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy pakiet, wskaż polecenie **Dodaj**, a następnie kliknij typ elementu.

         \- oraz

    - W Eksploratorze modelu UML przeciągnij istniejący element do pakietu.

         \- oraz

    - Połącz diagram z pakietem, a następnie utwórz elementy na diagramie.

         Aby to zrobić, kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij polecenie **Właściwości**. W oknie **Właściwości** Ustaw **połączony pakiet** z żądanym pakietem.

         Wszystkie nowe elementy, które tworzysz na diagramie, zostaną zdefiniowane w tym pakiecie.

         Można to zrobić tylko w przypadku niektórych typów diagramów.

## <a name="see-also"></a>Zobacz też
 [Zdefiniuj profil, aby zwiększyć UML](../modeling/define-a-profile-to-extend-uml.md) [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md)

