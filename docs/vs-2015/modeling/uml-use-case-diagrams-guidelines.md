---
title: 'Diagramy przypadków użycia UML: Wytyczne dotyczące | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b69a06f0dff7347e5f24899552f25721e71ee818
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780700"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramy przypadków użycia UML: Wytyczne dotyczące
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio, można narysować *diagram przypadków użycia* do podsumowania, który korzysta z aplikacji lub systemu i co zrobić z nim. Aby utworzyć diagram przypadków użycia UML, na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
 Aby obejrzeć wideo demonstracyjne, zobacz [organizowania funkcji do zastosowań](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Za pomocą diagramu przypadków użycia może omawianiu i komunikowaniu:  
  
- Scenariusze, w którym systemie lub aplikacji współdziała z osób, organizacji lub systemy zewnętrzne.  
  
- Cele, które ułatwia te podmioty osiągnąć.  
  
- Zakres systemu.  
  
  Diagram przypadków użycia nie są wyświetlane szczegóły przypadków użycia: podsumowuje tylko niektóre z relacji między przypadkami użycia, aktorów i systemów. W szczególności w schemacie nie są wyświetlane kolejność, w którym kroki są wykonywane w celu osiągnięcia celów każdego przypadku użycia. Możesz opisać te szczegóły przez inne diagramy i dokumentów, które można połączyć z poszczególnymi przypadkami użycia. Aby uzyskać więcej informacji, zobacz [opisujące przypadki użycia, szczegółowo](#Details) w tym temacie.  
  
  Opisy, podane dla przypadków użycia będzie używać kilku warunków związanych z domeną, w którym działa system, takich jak sprzedaż, Menu, klientów i tak dalej. Ważne jest, aby jasno zdefiniować te warunki i ich wzajemne relacje i możesz to zrobić za pomocą diagramu klas UML. Aby uzyskać więcej informacji, zobacz [diagramów klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md).  
  
  Zastosowań zajmować się wyłącznie wymagań dotyczących funkcjonalności systemu. Inne wymagania, takie jak reguły biznesowe, jakości wymagań dotyczących usług i ograniczeń wdrażania musi być reprezentowana oddzielnie. Architektura i szczegółami wewnętrznymi musi być opisane osobno. Aby uzyskać więcej informacji na temat sposobu definiowania wymagań użytkowników, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
  Przykłady używaną w tym temacie odnoszą się do witryny sieci Web, na którym klienci mogą zamówić posiłki z lokalnej restauracji.  
  
  ![Elementy na diagramie przypadku użycia](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
- *Aktora* (1) jest klasą osoby, organizacji, urządzenia lub składnik oprogramowania zewnętrznego, który wchodzi w interakcję z systemem. Przykład aktorów są **klienta**, **restauracji**, **czujnik temperatury**, **Autoryzatora karty kredytowej.**  
  
- A *przypadek użycia* (2) reprezentuje akcje, które są wykonywane przez jeden lub więcej podmiotów zgodnie z określonym celem. Przykładowe przypadki użycia są **zamówienie posiłku**, **Menu aktualizacji**, **przetwarzania płatności**.  
  
   Na diagramie przypadku użycia przypadki użycia są skojarzone (3) z uczestnikami, którzy je wykonywać.  
  
- Twoje *systemu [4]* jest cokolwiek tworzysz. Może być składnik małych oprogramowania, których podmioty są po prostu innych składników oprogramowania. lub może być kompletnej aplikacji; lub może być duży zestaw rozproszone aplikacje wdrożone przez wiele komputerów i urządzeń. Przykład podsystemy są **zamawianie posiłku witryny sieci Web**, **firm dostarczania posiłku**, **witryny sieci Web w wersji 2**.  
  
   Diagram przypadków użycia może być wyświetlany w przypadki użycia, które są obsługiwane przez system i podsystemów.  
  
##  <a name="BasicSteps"></a> Podstawowe kroki rysowania diagramów przypadków użycia  
  
> [!NOTE]
>  Szczegółowe kroki tworzenia dowolnego diagramu modelowania zawiera są opisane w [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>Aby utworzyć nowy diagram przypadków użycia  
  
1.  Na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
2.  W obszarze **szablony**, kliknij przycisk **Diagram przypadków UMLUse**.  
  
3.  Nadaj nazwę diagramowi.  
  
4.  W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania w rozwiązaniu, lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>Aby narysować diagram przypadków użycia  
  
1.  Przeciągnij **podsystemu** granice z przybornika do diagramu, do reprezentowania całego systemu lub jej główne składniki.  
  
    -   Możesz narysować diagram przypadków użycia, bez systemu granice, jeśli nie chcesz do opisywania, które przypadki użycia są obsługiwane przez system lub jego składniki.  
  
    -   Przeciągnij rogu systemu, aby powiększyć ją, jeśli to konieczne.  
  
    -   Odpowiednio zmienić jego nazwę.  
  
2.  Przeciągnij **aktorów** z przybornika do diagramu (umieszczenie ich poza granicami dowolnego systemu).  
  
    -   Aktorzy stanowią klasy użytkowników, organizacje i systemy zewnętrzne, które współdziałają z systemem.  
  
    -   Zmień ich nazwy. Na przykład: **Klient, restauracja, agencji karty kredytowej.**  
  
3.  Przeciągnij **przypadki użycia** z przybornika do odpowiednich systemów.  
  
    -   Zastosowań reprezentują działań, które aktorów wykonywać za pomocą systemu.  
  
    -   Zmień je za pomocą tytułów, czy zrozumiałą aktorów, samodzielnie. Nie należy używać tytułów, które są związane z Twoim kodem. Na przykład: **Zamówienie posiłku, płacisz posiłku, dostarczanie posiłku**.  
  
    -   Zaczynają się od głównych transakcji, takich jak **zamówienie posiłku**, opuścić aż do nowszych mniejszych interakcji, takich jak **wybierz element Menu**.  
  
    -   Przypadek użycia w każdym miejscu w systemie lub główne podsystem, który obsługuję (bez uwzględnienia wszelkich fasady lub składnika uwzględnionego tylko w przypadku nawiązywania połączenia użytkownika).  
  
    -   Możesz narysować przypadek użycia poza granicą systemu, aby pokazać, że jest nieobsługiwany przez system, prawdopodobnie w określonej wersji lub wydania.  
  
4.  Kliknij przycisk **skojarzenia** w przyborniku, a następnie przypadek użycia, a następnie aktora, który uczestniczy w przypadku użycia. Każdego aktora należy połączyć swoje przypadki użycia w ten sposób.  
  
5.  Struktura użycie przypadków z **Include**, **Rozszerz** i **Generalizacja** relacji. Aby utworzyć każdego z poniższych linków, kliknij narzędzie, a następnie źródła użycia, a następnie element docelowy. Zobacz następującą sekcję pod tytułem [struktury przypadki użycia](#Structuring).  
  
6.  Opisz przypadki użycia, które bardziej szczegółowo. Zobacz następującą sekcję pod tytułem [opisujące przypadki użycia, szczegółowo](#Details).  
  
7.  Rysuj oddzielnym diagramie, aby skoncentrować się na różnych podsystemów lub różnych grup powiązanych zastosowań. Wszystkie diagramy w jednym projekcie modelowania są widokami tego samego modelu.  
  
##  <a name="Actors"></a> Rysowanie aktorów i przypadki użycia  
 Głównym celem diagram przypadków użycia jest pokazanie, który korzysta z systemu i głównych celów, które osiągną z nim.  
  
-   Tworzenie **aktorów** do reprezentowania klasy osoby, organizacje, innych systemów, oprogramowania lub urządzeń, które współdziałają z systemu lub podsystemu.  
  
    -   Aby dowiedzieć się, jak narysować aktorów i innych elementów, zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
    -   Dla każdego zestawu różne cele zidentyfikować aktorów według ich typu lub roli, mimo że osób fizycznych lub jednostki mogą być takie same. Na przykład restauracji i odbiorcy są oddzielne aktorzy, nawet jeśli pracownik restauracji czasami może być klientem.  
  
-   Tworzenie **przypadki użycia** dla każdego cele, które każdego aktora stara się osiągnąć za pomocą systemu.  
  
    -   Nazwij i opisz przypadki użycia w wyrazy, które może zrozumieć aktora, zamiast warunki wdrożenia.  
  
-   Użyj **skojarzenia** połączyć aktorów z przypadkami użycia.  
  
### <a name="inheritance-between-actors"></a>Dziedziczenie między uczestnikami  
 ![Diagram przypadków użycia, wyświetlanie dziedziczenia](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 Można narysować **Generalizacja** łącza między uczestnikami. Wyspecjalizowane aktora, takich jak Club klienta, w tym przykładzie dziedziczy przypadki użycia uogólnionego aktora, takich jak klient. Strzałki powinien wskazywać na bardziej ogólnych aktora, takich jak klient. Gdy tworzysz link, wskaż najpierw bardziej wyspecjalizowane aktora.  
  
 Wyspecjalizowane aktora może mieć własną przypadków dodatkowe użycie, które nie są dostępne dla innych aktorów.  
  
> [!CAUTION]
>  Nie należy podejmować pętli relacji Generalizacja, które powoduje Aktor uogólnianie sam. Pętli może generować błędy.  
  
### <a name="alternative-actor-icons"></a>Ikony alternatywnych aktora  
 Niestandardowe ikony służy do reprezentowania aktora, zamiast standardowego kreska. Na przykład można zmienić go na podobny urządzenia, restauracji, bank i tak dalej.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>Aby zmienić wygląd aktora  
  
1.  Kliknij prawym przyciskiem myszy aktora, a następnie kliknij przycisk **właściwości**.  
  
     **Właściwości** zostanie wyświetlone okno.  
  
2.  Ustaw **ścieżka obrazu** właściwości do lokalizacji pliku obrazu.  
  
    -   Można użyć dowolnego z kilku formatów obrazu, w tym GIF, jpg i .bmp.  
  
    -   Użyj pliku, który znajduje się w rozwiązanie lub projekt do kontroli źródła, tak aby jest nadal dostępna, gdy rozwiązanie jest przenoszone lub kopiowane.  
  
3.  Do replikacji, to wygląd w inne diagramy przypadków użycia, aktor skopiować i wkleić go do innego diagramu.  
  
    -   Obrazu dotyczy tylko do widoku diagramu określonego. Nie ma zastosowania do podstawowego elementu modelu. Jeśli przeciągniesz aktora z Eksploratora modelu UML do innego diagramu, pojawi się jako standardowa kreska.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Liczebność punktów między podmiotami i przypadki użycia  
 Skojarzenie między aktora i przypadek użycia można wyświetlić *liczebność* na każdym końcu.  
  
 ![W przypadku jeden-do-jednego za pomocą aktora](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
>  Liczebność punktów skojarzenia na diagramie przypadków użycia są ukryte, jeśli są one zarówno **1**.  
  
 Domyślnie każdy liczebność jest **1**. Ścisłe interpretacji modelu liczebnością 1 oznacza, że, na przykład tylko jednego klienta są zaangażowane w kolejności każdy posiłek, i czy każdy klient porządkuje posiłku tylko jeden w danym momencie.  
  
 Możesz zmienić te Liczebność punktów.  
  
 Na przykład:  
  
 ![Przypadek użycia pokazujący liczebność wiele do wielu](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
- Do stanu, że kilka aktorów tej samej klasy mogą brać udział w pojedyncze wystąpienie przypadek użycia, na końcu aktora skojarzenie, aby ustawić liczebności ** 1... \\***.  
  
   Na ilustracji skorzystać z co najmniej jeden restauracji wypełniając takiej samej kolejności posiłku.  
  
- Aby pokazać, że każdego aktora mogą uczestniczyć w tym samym czasie w kilka wystąpień przypadek użycia, na końcu przypadków użycia skojarzenie, aby ustawić liczebności **\\***.  
  
   Na ilustracji każdy restauracji mogą pracować na spełniające więcej niż jedno ustawienie kolejności w danym momencie.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>Aby ustawić Liczebność punktów na skojarzenie  
  
1. Kliknij prawym przyciskiem myszy skojarzenia, a następnie kliknij przycisk **właściwości**.  
  
2. Rozwiń **pierwsza rola** lub **druga rola**.  
  
    *Rola* oznacza, że element na jednym końcu skojarzenia.  
  
3. Ustaw właściwość Multiplicity, wybierając z listy:  
  
   - **1** stwierdzić, że dokładnie jedno wystąpienie tej roli uczestniczy w każdym odnośniku.  
  
   - **1..\\*** do co najmniej jedno wystąpienie tej roli uczestniczyć w każdym odnośniku stanu.  
  
   - **od 0 do 1** do stanu, że udział jest opcjonalna.  
  
   - **\\*** Aby stwierdzać, że zero lub więcej wystąpień tej roli uczestniczyć w linku.  
  
> [!NOTE]
>  Wiele zespołów nie należy umieszczać informacje liczebność na diagramy przypadków użycia, pozostawiając Liczebność punktów na wartość domyślną 1. Zamiast tego zapewniają informacje przedstawione w osobnym opisy przypadki użycia. W takim przypadku zostaną ukryte wszystkich Liczebność punktów diagramy przypadków użycia.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Za pomocą przypadek aktora lub użyj na wiele diagramów  
 Można wyświetlić tych samych podmiotów i kilka diagramów przypadków użycia. Na przykład:  
  
-   Możesz opisać w różnych diagramach różnych zastosowań, w których uczestniczy jeden Aktor.  
  
-   Użyj jednym diagramie, aby pokazać aktorów i podsystemy, z którymi jest skojarzony przypadek użycia i użyj innego diagramu, aby pokazać, struktury przypadek użycia do przypadków użycia uwzględniona i rozszerzonej.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Aby wyświetlić ten sam aktora lub przypadek użycia w różnych diagramach  
  
1.  Utwórz aktora lub przypadek użycia na jednym diagramie.  
  
2.  Utwórz inny diagram przypadków użycia.  
  
3.  Przeciągnij aktora lub przypadek użycia poza **Eksploratora modelu** na nowego diagramu.  
  
    > [!NOTE]
    >  Jeśli umieścisz przy nowym diagramie aktora i przypadek użycia, które są już skojarzone, skojarzenie między nimi będzie wyświetlał nowego diagramu.  
  
##  <a name="Details"></a> Zastosowań szczegółowo opisujący  
 Reprezentuje przypadek użycia:  
  
- Celem aktora w systemie, takie jak **kupić posiłek**; oraz  
  
- Co najmniej jeden *scenariuszy*, czyli sekwencji czynności wykonywane w dążeniu do osiągnięcia celu, takich jak: {**zamówienie posiłku, płatności i dostarczanie**}. Oprócz scenariuszy sukcesu prawdopodobnie istnieje kilka scenariuszy awarii lub wyjątku takich jak **odrzucona karta kredytowa**.  
  
  Przypadek użycia może być opisany na różnych poziomach szczegółowości. Na wczesnym etapie projektowania wystarczy tylko nazwy na diagramie przypadków użycia.  Później można napisać bardziej szczegółowy opis scenariuszy.  
  
  W programie Visual Studio Ultimate można opisać przypadek użycia na kilka sposobów, które mogą być używane oddzielnie lub razem:  
  
- Połącz przypadek użycia do innego diagramu lub diagramy w projekcie.  
  
  -   Diagram aktywności pomaga wyjaśnić bardziej złożony proces w przypadku, gdy istnieją pętle i gałęzie równoległych wątków. Można również pokazać przepływ danych między części procesu. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
  -   Diagram sekwencji ułatwia wyjaśnić złożonych serię interakcji między różnymi uczestnikami. Można również użyć do wyświetlenia, co się dzieje w systemie w odpowiedzi do każdego przypadku użycia. Aby uzyskać więcej informacji, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
- Przypadek użycia połączyć strony programu OneNote, sekcji lub akapit, który opisuje przypadek użycia szczegółowo.  
  
- Przypadek użycia należy połączyć dokument programu Word, w której jest używany tekst, zrzuty ekranu i tak dalej do opisania scenariuszy przypadków użycia. Aby uzyskać więcej informacji, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Aby połączyć przypadek użycia na diagramie lub pliku w tym samym rozwiązaniu  
  
1.  Rysowanie diagramu, takich jak diagram sekwencji lub diagram aktywności, aby zilustrować scenariusza przypadku użycia.  
  
2.  Wróć do diagram przypadków użycia.  
  
3.  Przeciągnij na diagramie lub w pliku z Eksploratora rozwiązań na pustą część diagramu przypadków użycia.  
  
4.  Łączenie z artefaktu do przypadków użycia za pomocą **zależności**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Aby utworzyć łącze do pliku rozwiązania, takie jak dokument programu Word lub prezentacji programu PowerPoint  
  
1.  Zapis dokumentu, który używa tekstu, zrzuty ekranu i tak dalej do opisania scenariusza przypadku użycia.  
  
2.  Dodaj dokument do rozwiązania.  
  
    1.  W tym samym folderze Windows jako rozwiązanie, należy przenieść dokument programu Word.  
  
    2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący element**.  
  
    3.  Przejdź do dokumentu programu Word, a następnie kliknij przycisk **Dodaj**.  
  
         Dokument programu Word pojawia się w folderze rozwiązania w Eksploratorze rozwiązań.  
  
3.  Przeciągnij dokument programu Word za pomocą Eksploratora rozwiązań na pustą część diagramu przypadków użycia.  
  
     Pojawi się nowy artefaktu.  
  
4.  Łączenie z artefaktu do przypadków użycia za pomocą **zależności**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Aby utworzyć łącze do dokumentu udostępnionego, OneNote element lub strony sieci web  
  
1.  Uzyskaj adres URL udostępniony element. Może to być na przykład początku ścieżki pliku sieci "\\\\", lub strony sieci web lub początkowy adres URL programu Sharepoint "http://" lub łącze do sekcji programu OneNote, strony, akapitu początku "onenote:".  
  
2.  W przyborniku kliknij **artefaktu** a następnie kliknij przycisk na diagramie przypadku użycia.  
  
3.  Za pomocą nowego artefaktu wybrane, wpisz lub wklej adres URL do **hiperłącze** właściwości.  
  
> [!NOTE]
>  Możesz kliknąć dwukrotnie artefakt Otwórz diagram lub dokumentów, do której łączy.  
  
### <a name="linking-use-cases-to-work-items"></a>Łączenie przypadków użycia z elementami roboczymi  
 Jeśli projekt używa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] i masz [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], możesz połączyć każdego przypadku użycia elementu roboczego na [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Aby dowiedzieć się, jak te łącza, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).  
  
 Dzięki temu można:  
  
-   Opisano w przypadku użycia połączonego elementu roboczego. W szczególności jeśli projekt używa programu Visual Studio formalnego szablonu procesu, możesz połączyć element roboczy przypadku użycia. Ten typ elementu roboczego zawiera pola do opisywania celów i scenariuszy przypadków użycia.  
  
-   Połącz przypadki testowe z przypadek użycia, dzięki czemu można uzyskać raporty, w jakim kod opracowywane implementuje przypadek użycia.  
  
-   Łączenie zadań do przypadku użycia tak, aby można było śledzić postęp prac rozwojowych.  
  
##  <a name="Structuring"></a> Tworzenie struktury przypadki użycia  
 Należy próbować opisują zachowania systemu przy użyciu zaledwie kilku głównych zastosowań. Każdy przypadek użycia dużych definiuje cel główne, pozwalającej aktora, takich jak kupowanie produktu lub z punktu widzenia dostawcy oferuje produkty do sprzedaży.  
  
 Po dokonaniu tych celów, wyczyść możesz bardziej szczegółowo, jak uzyskuje się każdy cel i różnice w podstawowe cele.  
  
 Należy unikać podzielenie przypadki użycia zbyt szczegółowo. Przypadki użycia to środowisko użytkowników systemu, zamiast jego wewnętrzne działanie. Ponadto ogólnie znajdziesz je bardziej wydajnej pracy, aby utworzyć Wczesne wersje robocze kodu, zamiast wydatków czas tworzenia struktury przypadków użycia do szczegółowych informacji.  
  
 Na diagramie przypadku użycia można podsumować w relacji między przypadkami użycia głównych i bardziej szczegółowe. W poniższych sekcjach opisano to:  
  
-   [Wyświetlanie szczegółów przypadek użycia za pomocą dołączania](#Include)  
  
-   [Udostępnianie cele Generalizacja](#Inheritance)  
  
-   [Oddzielanie wariantu przypadków z rozszerzenie](#Extend)  
  
###  <a name="Include"></a> Wyświetlanie szczegółów przypadek użycia za pomocą dołączania  
 Użyj **Include** relacji, aby wyświetlić ten przypadek użycia jednego opisano niektóre szczegóły każdego innego. Na ilustracji **zamówienie posiłku** obejmuje **płacić**, **wybierz Menu**, i **wybierz element Menu**. Każdy z przypadkami użycia uwzględniona, bardziej szczegółowe jest krokiem, który aktora lub aktorów, może być konieczne przeprowadzenie do osiągnięcia celu ogólnej, w tym przypadku użycia. Strzałkę powinien wskazywać w przypadku użycia bardziej szczegółowe, dołączone.  
  
> [!CAUTION]
>  Nie należy podejmować pętli obejmują relacje, które powodują w przypadku użycia wraz z tym elementem. Pętle może powodować generowanie błędów.  
  
 Możesz udostępnić przypadki użycia uwzględniona. W tym przykładzie **zamówienie posiłku** i **subskrybować przeglądy** zastosowań oferują **płacić**.  
  
 ![Zastosowań rozłożone przy użyciu obejmują](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 Cel i scenariuszy przypadków użycia dołączony powinien sensu niezależnie, dzięki czemu może on być uwzględniony w przypadkach użycia, które zostały zaprojektowane w dalszej części.  
  
 Oddzielanie przypadki użycia w tym i części uwzględnione przydaje się do osiągnięcia następujących celów:  
  
-   Struktury opisów przypadków użycia w różnych warstwach szczegółów.  
  
-   Należy unikać powtarzania udostępnionego scenariuszy w różnych przypadków użycia.  
  
####  <a name="Steps"></a> Definiowanie kolejności szczegółowy opis kroków  
 Diagram przypadków użycia nie mówi nic o kolejność, w którym należy wykonać bardziej szczegółowy opis kroków, ani, czy każdy z nich zawsze jest konieczne.  
  
 Aby kolejność wyczyść kroki, możesz użyć **artefaktu** można dołączyć oddzielny dokument dotyczące przypadek użycia. W poniższym przykładzie diagram aktywności dołączone do zlecenia posiłku przypadek użycia. Alternatywnie można użyć dokument tekstowy, który zawiera listę kroków lub sekwencję zrzuty ekranu. Aby uzyskać więcej informacji, zobacz [opisujące przypadki użycia, szczegółowo](#Details).  
  
 Zwróć uwagę tych konwencji nazewnictwa, gdy używasz diagram aktywności:  
  
- Nazwa działania całego jest taka sama jak w tym przypadku użycia.  
  
- Akcje w diagramie aktywności ma takie same nazwy dołączonej przypadki użycia.  
  
  Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
  ![Wykonaj kroki wielkości liter pokazano na diagramie połączone działanie](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
###  <a name="Inheritance"></a> Udostępnianie cele Generalizacja  
 Użyj relację generalizacji, aby pokazać, że *wyspecjalizowane* przypadkiem użycia jest określony sposób, aby osiągnąć cele wyrażona przez inny *ogólne* przypadek użycia. Otwórz grot strzałki powinien wskazywać na bardziej ogólnych przypadek użycia.  
  
 ![Zastosowań przedstawiający relację generalizacji](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Na przykład **płacić** uogólnia **zapłacić kartą kredytową** i **płacić za**.  
  
> [!CAUTION]
>  Nie należy podejmować pętli relacji Generalizacja prowadzących Aktor uogólnianie sam. Pętli może generować błędy.  
  
 Zastosowań specjalnych może pomóc w przedstawiono różne sposoby, że system może osiągnąć ten sam cel.  
  
 Przypadki użycia specjalne są traktowane jako dziedziczą cele i aktorami ogólne przypadek użycia. Przypadek użycia ogólne musi mieć swój własny; scenariusze jego specjalizacji opisano różne sposoby realizacji celów.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Refaktoryzacja wspólnych celów z co najmniej dwa przypadki użycia  
  
1.  Utwórz i nazwy ogólne nowy przypadek użycia.  
  
2.  Tworzenie **Generalizacja** relacji o dużych strzałka wskazująca w nowym przypadku użycia ogólne.  
  
    1.  Kliknij przycisk **Generalizacja** w przyborniku.  
  
    2.  Kliknij przycisk przypadek użycia wyspecjalizowane (**zapłacić kartą kredytową** w przykładzie).  
  
    3.  Kliknij przycisk przypadek użycia ogólne (**płacić** w przykładzie).  
  
3.  Jeśli mają opisano cele dla przypadków użycia specjalistyczne, Przenieś przypadków użycia wspólnego części w opisie ogólne.  
  
4.  Aktorów, które są współużytkowane między przypadkami użycia wyspecjalizowane mogą być przenoszone do przypadku użycia ogólne.  
  
###  <a name="Extend"></a> Oddziel wariantu przypadkach rozszerzenie  
 Użyj linku rozszerzenie, aby pokazać, że jeden przypadek użycia może dodać funkcje do innego przypadku użycia w pewnych okolicznościach. Strzałkę powinien wskazywać na przypadek użycia głównym, rozszerzoną.  
  
 ![Przypadek użycia jednej, innej rozszerzanie](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
>  Nie należy podejmować pętli rozszerzyć relacji prowadzących Aktor uogólnianie sam. Pętli może generować błędy.  
  
 Na przykład **logowania** przypadek użycia typowych witryny sieci Web mogą zawierać **rejestrowanie nowego użytkownika** —, ale tylko po użytkownik nie ma jeszcze konta usługi.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Do oddzielania przypadek użycia w części głównej i rozszerzanie  
  
1. Utwórz i przypadek użycia nazwy nowego rozszerzenia.  
  
2. Tworzenie **Rozszerz** relacji o strzałka wskazująca w przypadku rozszerzonego użycia.  
  
   1.  Kliknij przycisk **Rozszerz** w przyborniku.  
  
   2.  Kliknij przycisk rozszerzanie przypadek użycia (**rejestrowanie nowego użytkownika** w przykładzie).  
  
   3.  Kliknij przycisk przypadku rozszerzonego użycia (**logowania** w przykładzie).  
  
       > [!NOTE]
       >  Unikaj tworzenia pętlę relacji rozszerzenie na diagramie. Jest niepoprawny dla przypadek użycia jako rozszerzenie samego siebie.  
  
3. Jeśli masz już utworzoną rozszerzone scenariusze przypadków użycia, Przenieś odpowiednie kroki w scenariuszu rozszerzenia.  
  
4. Opis rozszerzenia (**rejestrowanie nowego użytkownika** w przykładzie) powinna zawierać szczegóły gdzie głównych scenariuszy przypadków użycia wystąpi ona i w jakich okolicznościach. Go traktować jako modyfikowanie opis przypadku głównym.  
  
   Przypadek użycia rozszerzenia reprezentuje kroki w scenariuszu, które w przeciwnym razie będą częścią scenariuszy przypadków użycia głównego. Scenariusz i celem rozszerzenia będą zawsze można odczytać w kontekście przypadek użycia głównego, w związku z tym nie mają być przydatne niezależnie.  
  
   Oddzielanie rozszerzenia może być przydatne do opisywania tych sytuacji:  
  
-   Brak dodatkowych aktorów, którzy są zaangażowani tylko w przypadku użycia rozszerzenia. Na przykład administrator musi zatwierdzić rejestracji klienta w witrynie sieci Web.  
  
-   Oddzielne podsystemu poradzi sobie z przypadkami użycia rozszerzenia.  
  
-   Rozszerzenie to będzie dostępna tylko w określonych wersjach systemu. Każda wersja można wyświetlić jako osobne podsystem na diagramie przypadku użycia.  
  
##  <a name="Subsystems"></a> Za pomocą podsystemu granice  
 Użyj granicą podsystemu, aby pokazać, co przypadki użycia znajdują się w zakresie systemu.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>Aby narysować granicą podsystemu  
  
1. W przyborniku kliknij **podsystemu**, następnie kliknij przycisk diagramu.  
  
    Podsystem pojawia się na diagramie.  
  
2. Przeciągnij narożniki, podsystemu, aby dostosować jego rozmiar.  
  
3. Przeciągnij istniejące przypadki użycia do lub z podsystemu, aby dostosować jego zawartość.  
  
   \- lub —  
  
   Aby utworzyć nowy przypadek użycia bezpośrednio w podsystemie, kliknij przycisk **przypadek użycia** w przyborniku, następnie kliknij wewnątrz podsystemu.  
  
> [!NOTE]
>  **Przedmioty** właściwości przypadku użycia wskazuje, jakie podsystemu znajduje się w.  
  
### <a name="use-cases-outside-the-system-scope"></a>Przypadki użycia poza zakresem systemu  
 Jest często przydatny diagram przypadków użycia, które należą do firmy, ale nie zajmuje się przez system, który tworzysz. Dzięki temu deweloperzy rozumiesz jeszcze kontekst ich pracy. Na przykład dostarczanie posiłku można pokazać jako przypadek użycia udziałem aktorów restauracjach i klienta, ale poza programem odpowiedzialność z posiłku porządkowanie witryny sieci Web.  
  
### <a name="multiple-subsystems"></a>Wiele podsystemów  
 Można utworzyć kilka granice podsystemu pokazanie użycia jak różne przypadki są prowadzone przez różne składniki systemu. Na przykład **Dodawanie oceny restauracji** mogą być rozpatrywane w witrynie sieci Web w osobnych forum. Należy pamiętać, diagram przypadków użycia powinno dotyczyć co to jest widoczny dla użytkownika. Jeśli użytkownik chce opisać wewnętrznego podziału pracy w systemie, rozważ użycie diagram składników.  
  
### <a name="system-versions"></a>Wersje systemu  
 Granice różnych podsystemu umożliwia pokazują różne wersje systemu. Na przykład płatność przypadek użycia mógłby być zawarty w witrynie sieci Web w wersji 2, ale nie w wersji 1. oznacza to, czy system pomaga klientom w ich zamówień. Jednakże muszą oni bezpośrednio płatności restauracji.  
  
 Użyj **zależności** relacji połączyć podsystemów reprezentująca różne wersje lub wariantów.  
  
 ![Podsystemy pokazujące różne wersje systemu](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md)   
 [Wideo: Organizowanie funkcji w przypadki użycia](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)
