---
title: Łączenie elementów modeli i elementów roboczych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cdfcb6bb07f167ea1da81101ae00613a5b2fac93
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440961"
---
# <a name="link-model-elements-and-work-items"></a>Łączenie elementów modeli i elementów roboczych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Śledź zadania, przypadki testowe, błędy, wymagania, problemy i inne zadania związane z modelu, łącząc elementy modelu w programie Visual Studio i elementów roboczych w Team Foundation Server lub Visual Studio Team Services. Dołącz dokumenty do połączonych elementów roboczych, aby skojarzyć je z elementami modelu.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
> Aby utworzyć i otworzyć łącza, należy użyć programu Team Explorer. Upewnij się, że projekt modelowania i diagramy są sprawdzane w ramach kontroli wersji, tak aby inni użytkownicy mogli otworzyć diagramy połączone.  
  
 Można na przykład połączyć:  
  
- Element roboczy historii użytkownika i diagram aktywności, aby pokazać, jak zrealizować historię za pomocą sekwencji operacji.  
  
- Przypadek użycia na diagramie przypadków użycia z elementami roboczymi przypadków testowych, aby upewnić się, że przypadek użycia jest poprawnie zaimplementowany.  
  
- Atrybut w klasie na diagramie klas UML z elementem roboczym usterki, aby pokazać błąd w implementacji atrybutu.  
  
- Składnik na diagramie składników z elementem roboczym zadania, w celu śledzenia rozwoju składnika. Takie zadanie zazwyczaj jest dzielone na mniejsze zadania.  
  
  Elementy robocze można połączyć z dowolnym elementem dostępnym do wybrania na diagramach modelowania lub w Eksploratorze modelu UML, jak na przykład:  
  
- Wszystkie elementy w modelach UML, takie jak klasy UML, linie życia, przypadki użycia, podsystemy, aktywności, węzły obiektów, składniki, interfejsy  
  
- Wszystkie relacje w modelach UML, takie jak skojarzenia, generalizacje, zależności, przepływy, wiadomości  
  
- Części elementów, takie jak atrybuty i operacje klas, wystąpienia wykonywania linii życia, piny wejściowe i wyjściowe aktywności oraz części i porty składników  
  
- Warstwy i zależności warstw  
  
- Komentarze i łącza do komentarzy  
  
- Diagramy. Aby wybrać diagram, wybierz jego pustą część.  
  
> [!WARNING]
> Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.  
  
- [Połącz z projektem zespołowym](#ConnectTFS)  
  
- [Połącz element modelu z nowego elementu roboczego](#LinkNew)  
  
- [Połącz element modelu z istniejącym elementem pracy](#LinkExisting)  
  
- [Wyświetl elementy robocze połączone z elementem modelu](#OpenWorkItem)  
  
- [Wyświetl elementy modelu połączone z elementem roboczym](#ViewLinkedModels)  
  
- [Usuń łącza między elementami modelu i elementami roboczymi](#RemoveLinks)  
  
- [Rozwiązywanie problemów](#Troubleshooting)  
  
## <a name="ConnectTFS"></a> Połącz z projektem zespołowym  
 Musisz najpierw połączyć się z projektem zespołowym do tworzenia, wyświetlania lub usuwania łączy.  
  
1. Na **zespołu** menu, wybierz **Zarządzaj połączeniami** do wyświetlenia okna programu Team Explorer.  
  
2. Jeśli odpowiedni projekt nie pojawia się w programie Team Explorer wybierz **Zarządzaj połączeniami** , a następnie wybierz **Połącz z projektem zespołowym**. Następnie wybierz w razie potrzeby odpowiednie projekty lub serwer.  
  
3. W **Team Explorer**, wybierz projekt, w którym chcesz utworzyć, połączyć lub wyświetlać elementy robocze.  
  
## <a name="LinkNew"></a> Połącz element modelu z nowego elementu roboczego  
  
1. Upewnij się, że masz połączenie z wystąpieniem TFS, którego chcesz użyć.  
  
2. Na diagramie modelowania lub w **Eksploratora modelu UML**, otwórz menu skrótów dla elementu modelu.  
  
3. Wybierz **Utwórz element pracy** i rodzaj elementu roboczego, który chcesz utworzyć.  
  
4. Wypełnij pola formularza elementu roboczego. Wybierz **Zapisz element roboczy**.  
  
     Program Visual Studio połączy element modelu z nowym elementem roboczym. Ikona pojawi się na elemencie modelu lub w pobliżu.  
  
> [!WARNING]
> Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.  
  
## <a name="LinkExisting"></a> Połącz element modelu z istniejącym elementem pracy  
 Podczas łączenia elementów modelu z elementami roboczymi należy rozpocząć od elementu modelu, a nie od elementu roboczego.  
  
1. Upewnij się, że masz połączenie z wystąpieniem TFS, którego chcesz użyć.  
  
2. Na diagramie modelowania lub w **Eksploratora modelu UML**, otwórz menu skrótów dla elementu modelu. Wybierz **Połącz z elementem roboczym**. Następnie wybierz swój projekt w **projektu** pola.  
  
3. Wybierz jeden lub więcej elementów roboczych, aby utworzyć łącze do elementu modelu, wykonując jedną z następujących czynności:  
  
    - Wybierz zapytanie w **zapisane zapytanie**.  
  
    - Wpisz identyfikatory elementów roboczych, rozdzielone spacjami, w **identyfikatory**.  
  
    - Wpisz odpowiednie słowo lub frazę w **tytuł zawiera**.  
  
4. Wybierz **znaleźć**.  
  
5. Na liście elementów roboczych wybierz jeden z nich lub kilka, które chcesz połączyć.  
  
     Gdy wszystko będzie gotowe, **elementów roboczych** właściwości elementu modelu pokazuje liczbę większą niż wcześniej. Ikona pojawi się również na elemencie modelu lub w pobliżu.  
  
> [!WARNING]
> Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.  
  
## <a name="OpenWorkItem"></a> Wyświetl elementy robocze połączone z elementem modelu  
  
1. W **Team Explorer**, upewnij się, że nawiązano do projektu zespołowego, gdzie elementy robocze są połączone z elementem modelu.  
  
2. Na diagramie modelowania lub w **Eksploratora modelu UML**, otwórz menu skrótów dla elementu modelu. Wybierz **Wyświetl elementy robocze** Aby wyświetlić listę połączonych elementów roboczych.  
  
    > [!NOTE]
    > Wyświetlane są tylko elementy robocze z aktualnie połączonego serwera. Jeśli nie widzisz żadnych elementów roboczych, upewnij się, że łączysz się z właściwym serwerem w programie **Team Explorer**.  
  
## <a name="ViewLinkedModels"></a> Wyświetl elementy modelu połączone z elementem roboczym  
 Można wyświetlić diagramy modelowania i elementy, które są połączone z elementem roboczym w programie Visual Studio Team Services i w Team Foundation Server 2012 lub nowszym. Na przykład element roboczy może być połączony z modelami klas, które pokazują projekt nowych klas, które mają być zaimplementowane.  
  
1. W **Team Explorer**, upewnij się, że nawiązano do projektu zespołowego, gdzie elementy modelu są połączone z elementem roboczym.  
  
    > [!NOTE]
    > Do wyświetlania elementów modelu połączonego można używać tylko programu Team Explorer, a nie Team Web Access. Upewnij się, że obszar roboczy jest mapowany do projektu modelowania, zawierającego elementy lub diagramy modelowania. Jeśli nie masz obszaru roboczego, należy go utworzyć. Zobacz [Rozwiązywanie problemów](#Troubleshooting) i [tworzenie i Praca z obszarami roboczymi](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).  
  
2. Otwórz element roboczy, wybierz polecenie **łącza**. W obszarze **łącze modelu**, otwórz menu skrótów dla połączonego elementu modelu. Wybierz **Otwórz połączony element**.  
  
     ![Otwórz połączonego elementu modelu z elementu roboczego](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")  
  
## <a name="RemoveLinks"></a> Usuń łącza między elementami modelu i elementami roboczymi  
 Usuń połączony element roboczy przez uruchomienie z elementu modelu. W ten sposób można poprawnie usunąć wzajemne powiązania z tym elementem modelu z elementu roboczego. W przeciwnym razie, jeśli zaczniesz od elementu roboczego, nie będzie można usunąć wzajemnego powiązania z tym elementem roboczym z elementu modelu.  
  
1. Na diagramie modelowania lub w **Eksploratora modelu UML**, otwórz menu skrótów dla elementu modelu.  
  
2. Wybierz **usuwa elementy robocze**.  
  
     \- lub —  
  
    1. Wybierz **właściwości**, następnie **elementy robocze** gdzie jest wyświetlana liczba połączonych elementów roboczych.  
  
    2. W **elementów roboczych** właściwości, wybierz przycisk wielokropka **[...]** .  
  
        > [!NOTE]
        > Pojawiają się tylko elementy robocze na bieżącym serwerze. Jeśli lista jest pusta, ale liczba elementów roboczych nie jest równa zeru, upewnij się, że nawiązano połączenie z właściwym serwerem w **Team Explorer**.  
  
3. W obszarze **Usuń łącza do elementów roboczych**, wyczyść wybrane elementy, które chcesz odłączyć. Wybierz **OK**.  
  
## <a name="Troubleshooting"></a> Rozwiązywanie problemów  
  
|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|  
|---------------|------------------------|--------------------|  
|Nie można odnaleźć elementu modelu, który chcesz połączyć.|Element może znajdować się na diagramie w projekcie modelowania, który znajduje się w [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Możliwe, że nie masz obszaru roboczego, który jest mapowany do diagramu.|Zmapuj obszar roboczy projektu modelowania i diagram. Jeśli nie masz obszaru roboczego, należy go utworzyć.<br /><br /> Komunikat o błędzie wyświetlany dla tego problemu zawiera ścieżkę, która służy do mapowania obszaru roboczego.<br /><br /> Zobacz [tworzenie i Praca z obszarami roboczymi](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|  
|Nie można odnaleźć połączonego elementu modelu.|Połączony element może znajdować się na diagramie, który został przeniesiony, zmieniony lub usunięty.|1.  W elemencie roboczym usuń łącze do elementu modelu.<br />2.  Utwórz nowe łącze od elementu roboczego do elementu modelu.|  
|Element roboczy nie pokazuje oczekiwanych, połączonych elementów modelu.|Element roboczy pokazuje element warstwy połączonej, tylko jeśli łącze zostało utworzone z elementu roboczego. Jeśli Twój zespół nie używa [!INCLUDE[esprscc](../includes/esprscc-md.md)], ścieżki lokalne diagramów będą służyć do tworzenia linków. Jeśli projekt modelowania i jego diagramy są w [!INCLUDE[esprscc](../includes/esprscc-md.md)], wszyscy członkowie zespołu mający dostęp do projektu mogą wyświetlić połączone elementy w elementach roboczych.|Spróbuj odświeżyć element roboczy.|  
|Usuwanie łącza do elementu modelu z elementu roboczego nie spowodowało usunięcia łącza od elementu modelu do elementu roboczego.||Usuń łącze do elementu roboczego, zaczynając od elementu modelu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
