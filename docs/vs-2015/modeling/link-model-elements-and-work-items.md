---
title: Łączenie elementów modelu i elementów roboczych | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657628"
---
# <a name="link-model-elements-and-work-items"></a>Łączenie elementów modeli i elementów roboczych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Śledź zadania, przypadki testowe, usterki, wymagania, problemy i inne prace związane z modelem przez łączenie elementów modelu w programie Visual Studio i elementów roboczych w Team Foundation Server lub Visual Studio Team Services. Dołącz dokumenty do połączonych elementów roboczych, aby skojarzyć je z elementami modelu.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Aby utworzyć i otworzyć linki, należy użyć Team Explorer. Upewnij się, że projekt modelowania i diagramy są sprawdzane w ramach kontroli wersji, tak aby inni użytkownicy mogli otworzyć diagramy połączone.

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
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

- [Nawiązywanie połączenia z projektem zespołowym](#ConnectTFS)

- [Połącz element modelu z nowym elementem roboczym](#LinkNew)

- [Połącz element modelu z istniejącym elementem roboczym](#LinkExisting)

- [Wyświetl elementy robocze połączone z elementem modelu](#OpenWorkItem)

- [Wyświetl elementy modelu połączone z elementem roboczym](#ViewLinkedModels)

- [Usuwanie linków między elementami modelu i elementami roboczymi](#RemoveLinks)

- [Rozwiązywanie problemów](#Troubleshooting)

## <a name="connect-to-a-team-project"></a><a name="ConnectTFS"></a> Nawiązywanie połączenia z projektem zespołowym
 Musisz najpierw połączyć się z projektem zespołowym, aby tworzyć, wyświetlać lub usuwać linki.

1. W menu **zespół** wybierz polecenie **Zarządzaj połączeniami** , aby wyświetlić okno Team Explorer.

2. Jeśli odpowiedni projekt nie jest wyświetlany, w obszarze Team Explorer wybierz pozycję **Zarządzaj połączeniami** , a następnie wybierz pozycję **Połącz z projektem zespołowym**. Następnie wybierz w razie potrzeby odpowiednie projekty lub serwer.

3. W **Team Explorer**wybierz projekt, w którym chcesz utworzyć, połączyć lub wyświetlić elementy robocze.

## <a name="link-a-model-element-to-a-new-work-item"></a><a name="LinkNew"></a> Połącz element modelu z nowym elementem roboczym

1. Upewnij się, że nawiązano połączenie z wystąpieniem TFS, którego chcesz użyć.

2. Na diagramie modelowania lub w **Eksploratorze modelu UML**Otwórz menu skrótów dla elementu modelu.

3. Wybierz pozycję **Utwórz element roboczy** i rodzaj elementu pracy, który chcesz utworzyć.

4. Wypełnij pola formularza elementu roboczego. Wybierz pozycję **Zapisz element roboczy**.

     Program Visual Studio połączy element modelu z nowym elementem roboczym. Ikona pojawi się na elemencie modelu lub w pobliżu.

> [!WARNING]
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

## <a name="link-a-model-element-to-an-existing-work-item"></a><a name="LinkExisting"></a> Połącz element modelu z istniejącym elementem roboczym
 Podczas łączenia elementów modelu z elementami roboczymi należy rozpocząć od elementu modelu, a nie od elementu roboczego.

1. Upewnij się, że nawiązano połączenie z wystąpieniem TFS, którego chcesz użyć.

2. Na diagramie modelowania lub w **Eksploratorze modelu UML**Otwórz menu skrótów dla elementu modelu. Wybierz **łącze do elementu pracy**. Następnie wybierz projekt w polu **projekt** .

3. Wybierz jeden lub więcej elementów roboczych, aby utworzyć łącze do elementu modelu, wykonując jedną z następujących czynności:

    - Wybierz zapytanie w **zapisanej kwerendzie**.

    - Wpisz identyfikatory co najmniej jednego elementu pracy, rozdzielone spacjami w polu **identyfikatory**.

    - Wpisz słowo lub frazę w **tytule zawiera**.

4. Wybierz pozycję **Znajdź**.

5. Na liście elementów roboczych wybierz jeden z nich lub kilka, które chcesz połączyć.

     Gdy wszystko będzie gotowe, właściwość **elementy robocze** elementu model pokazuje większą liczbę niż poprzednio. Ikona pojawi się również na elemencie modelu lub w pobliżu.

> [!WARNING]
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

## <a name="view-work-items-linked-to-a-model-element"></a><a name="OpenWorkItem"></a> Wyświetl elementy robocze połączone z elementem modelu

1. W **Team Explorer**upewnij się, że masz połączenie z projektem zespołowym, w którym elementy robocze są połączone z elementem modelu.

2. Na diagramie modelowania lub w **Eksploratorze modelu UML**Otwórz menu skrótów dla elementu modelu. Wybierz pozycję **Wyświetl elementy robocze** , aby wyświetlić listę połączonych elementów roboczych.

    > [!NOTE]
    > Wyświetlane są tylko elementy robocze z aktualnie połączonego serwera. Jeśli nie widzisz żadnych elementów roboczych, upewnij się, że nawiązano połączenie z właściwym serwerem w **Team Explorer**.

## <a name="view-model-elements-linked-to-a-work-item"></a><a name="ViewLinkedModels"></a> Wyświetl elementy modelu połączone z elementem roboczym
 Można wyświetlić diagramy modelowania i elementy, które są połączone z elementem roboczym w Visual Studio Team Services i w Team Foundation Server 2012 lub nowszym. Na przykład element roboczy może być połączony z modelami klas, które pokazują projekt nowych klas, które mają być zaimplementowane.

1. W **Team Explorer**upewnij się, że masz połączenie z projektem zespołowym, w którym elementy modelu są połączone z elementem roboczym.

    > [!NOTE]
    > Do wyświetlania elementów modelu połączonego można używać tylko programu Team Explorer, a nie Team Web Access. Upewnij się, że obszar roboczy jest mapowany do projektu modelowania, zawierającego elementy lub diagramy modelowania. Jeśli nie masz obszaru roboczego, należy go utworzyć. Zobacz temat [Rozwiązywanie problemów](#Troubleshooting) i [Tworzenie i współpraca z obszarami roboczymi](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. Otwórz element roboczy, wybierz **linki**. W obszarze **łącze modelu**Otwórz menu skrótów dla połączonego elementu modelu. Wybierz pozycję **Otwórz połączony element**.

     ![Otwórz połączony element modelu z elementu pracy](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="delete-links-between-model-elements-and-work-items"></a><a name="RemoveLinks"></a> Usuwanie linków między elementami modelu i elementami roboczymi
 Usuń połączony element roboczy przez uruchomienie z elementu modelu. W ten sposób można poprawnie usunąć wzajemne powiązania z tym elementem modelu z elementu roboczego. W przeciwnym razie, jeśli zaczniesz od elementu roboczego, nie będzie można usunąć wzajemnego powiązania z tym elementem roboczym z elementu modelu.

1. Na diagramie modelowania lub w **Eksploratorze modelu UML**Otwórz menu skrótów dla elementu modelu.

2. Wybierz pozycję **Usuń elementy robocze**.

     \- oraz

    1. Wybierz **Właściwości**, a następnie **elementy robocze** , w których zostanie wyświetlona liczba połączonych elementów roboczych.

    2. W właściwości **elementy robocze** wybierz przycisk wielokropka **[...]**.

        > [!NOTE]
        > Pojawiają się tylko elementy robocze na bieżącym serwerze. Jeśli lista jest pusta, ale liczba elementów roboczych jest różna od zera, upewnij się, że nawiązano połączenie z właściwym serwerem w **Team Explorer**.

3. W obszarze **Usuń linki do elementów roboczych**Wyczyść wybrane elementy, które chcesz odłączyć. Wybierz przycisk **OK**.

## <a name="troubleshooting"></a><a name="Troubleshooting"></a> Rozwiązywanie problemów z

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|---------------|------------------------|--------------------|
|Nie można odnaleźć elementu modelu, który chcesz połączyć.|Element może znajdować się na diagramie w projekcie modelowania, który znajduje się w [!INCLUDE[esprscc](../includes/esprscc-md.md)] . Możliwe, że nie masz obszaru roboczego, który jest mapowany do diagramu.|Zmapuj obszar roboczy projektu modelowania i diagram. Jeśli nie masz obszaru roboczego, należy go utworzyć.<br /><br /> Komunikat o błędzie wyświetlany dla tego problemu zawiera ścieżkę, która służy do mapowania obszaru roboczego.<br /><br /> Zobacz [Tworzenie i współpraca z obszarami roboczymi](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|Nie można odnaleźć połączonego elementu modelu.|Połączony element może znajdować się na diagramie, który został przeniesiony, zmieniony lub usunięty.|1. w elemencie roboczym Usuń łącze do elementu modelu.<br />2. Utwórz nowe łącze od elementu pracy do elementu modelu.|
|Element roboczy nie pokazuje oczekiwanych, połączonych elementów modelu.|Element roboczy pokazuje element warstwy połączonej, tylko jeśli łącze zostało utworzone z elementu roboczego. Jeśli Twój zespół nie używa [!INCLUDE[esprscc](../includes/esprscc-md.md)] , ścieżka lokalna diagramów zostanie użyta do utworzenia linków. Jeśli projekt modelowania i jego diagramy znajdują się w [!INCLUDE[esprscc](../includes/esprscc-md.md)] , wszyscy członkowie zespołu, którzy mogą uzyskać dostęp do projektu, mogą wyświetlać połączone elementy w elementach roboczych.|Spróbuj odświeżyć element roboczy.|
|Usuwanie łącza do elementu modelu z elementu roboczego nie spowodowało usunięcia łącza od elementu modelu do elementu roboczego.||Usuń łącze do elementu roboczego, zaczynając od elementu modelu.|

## <a name="see-also"></a>Zobacz też
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)
