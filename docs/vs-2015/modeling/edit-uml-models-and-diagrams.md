---
title: Edytowanie modeli i diagramów UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295525"
---
# <a name="edit-uml-models-and-diagrams"></a>Edytowanie modeli i diagramów UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz tworzyć i edytować model UML za pomocą widoków udostępnianych przez kilka różnych typów diagramów. Dzięki zapewnieniu różnych perspektyw w systemie te diagramy ułatwiają zrozumienie i omawianie różnych aspektów projektu i wymagań. Program Visual Studio udostępnia szablony dla pięciu najczęściej używanych typów diagramu UML.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 W tym temacie opisano techniki umożliwiające edytowanie modelu, który jest wspólny dla różnych typów diagramów. Aby uzyskać więcej informacji, które są specyficzne dla określonych typów diagramów, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>W tym temacie

- [Diagramy UML są widokami modelu UML](#Views)

- [Tworzenie diagramów modelowania UML](#Creating)

- [Rysowanie diagramów modelowania UML](#Drawing)

- [Edytowanie kształtów i łączników](#Editing)

- [Cofanie zmian w modelu](#Undo)

- [Udostępnianie elementów między diagramami](#Sharing)

- [Kopiowanie elementów i grup elementów pokrewnych](#Copying)

- [Usuwanie elementu modelu lub jego widoków](#Deleting)

- [Wyszukiwanie tekstu w diagramie](#Searching)

- [Przygotowywanie diagramu do prezentacji](#presentation)

- [Rozszerzanie projektantów UML](#extensions)

## <a name="uml-diagrams-are-views-of-a-uml-model"></a><a name="Views"></a> Diagramy UML są widokami modelu UML
 Diagramy UML można tworzyć i używać tylko w projektach modelowania. Aby uzyskać więcej informacji na temat tworzenia diagramów i projektów, zobacz [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Projekt modelowania zawiera jeden model UML. Każdy diagram UML w projekcie jest widokiem modelu UML.

- Model można zobaczyć w **Eksploratorze modelu UML**. W menu **Architektura** wskaż polecenie **Windows**, a następnie kliknij pozycję **Eksplorator modelu UML**.

- Każdy kształt na diagramie jest widokiem elementu w modelu. Po umieszczeniu nowego kształtu na diagramie tworzony jest nowy element w modelu.

- Podczas zapisywania dowolnego diagramu program Visual Studio zapisuje cały model, wszystkie jego diagramy i plik projektu modelowania.

## <a name="creating-uml-modeling-diagrams"></a><a name="Creating"></a> Tworzenie diagramów modelowania UML

1. W menu **Architektura** w programie Visual Studio kliknij pozycję **Nowy UML lub diagram warstwowy**.

2. Wybierz diagram i nadaj mu nazwę.

3. W obszarze **Dodaj do projektu modelowania**wybierz istniejący projekt modelowania lub wybierz opcję **Utwórz nowy projekt modelowania**.

   > [!NOTE]
   > Diagram modelowania musi znajdować się w projekcie modelowania.

   Możesz również dodać diagram do istniejącego projektu modelowania w Eksplorator rozwiązań. Kliknij prawym przyciskiem myszy projekt modelowania, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Aby utworzyć pusty projekt modelowania UML

- W menu **plik** wskaż polecenie **Nowy**, kliknij pozycję **projekt**, a następnie w oknie dialogowym **Nowy projekt** kliknij dwukrotnie pozycję **projekty modelowania**.

  Aby uzyskać więcej informacji o sposobach zarządzania projektami modelowania, zobacz [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="drawing-uml-modeling-diagrams"></a><a name="Drawing"></a> Rysowanie diagramów modelowania UML
 Na diagramie modelowania jest wyświetlana Kolekcja elementów modelu połączonych przez relacje. Każdy element jest wyświetlany jako kształt, a każda relacja jest wyświetlana jako łącznik między dwoma kształtami.

 Istnieją dwa rodzaje narzędzi — jeden dla elementów i jeden dla relacji. Na przykład, w przyborniku Diagram klas UML, **Klasa** jest narzędziem elementu, a **skojarzenie** jest narzędziem relacji.

> [!NOTE]
> Jeśli chcesz uzyskać informacje specyficzne dla konkretnych typów diagramów, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Aby utworzyć elementy i relacje na diagramie modelowania UML

1. Aby utworzyć element modelu, kliknij narzędzie elementu w przyborniku, a następnie kliknij diagram, w którym ma się pojawić. Po utworzeniu elementu Dostosuj jego rozmiar i kształt, przeciągając jego uchwyty.

    W niektórych przypadkach można umieścić nowy element wewnątrz innego elementu. Na przykład na diagramie klasy UML można umieścić klasę wewnątrz pakietu.

   > [!NOTE]
   > Jeśli Przybornik nie jest widoczny, kliknij polecenie **Przybornik** w menu **Widok** .

2. Aby utworzyć relację, kliknij narzędzie relacji, kliknij element, w którym ma się rozpocząć relacja, a następnie kliknij element, w którym ma się zakończyć.

    Różne typy relacji mogą być uruchamiane lub kończyć się różnymi typami elementów. Na przykład na diagramie klasy UML relacja skojarzenia nie może rozpoczynać się ani kończyć na elemencie Comment.

   > [!NOTE]
   > Aby użyć tego samego narzędzia kilka razy, kliknij je dwukrotnie. Po zakończeniu kliknij narzędzie **wskaźnik** .

   W przypadku niektórych rodzajów diagramów można również rysować proste kształty. Te kształty nie są częścią modelu, ale można ich używać do rysowania uwagi do części diagramu lub do dzielenia go na różne obszary.

## <a name="editing-shapes-and-connectors"></a><a name="Editing"></a> Edytowanie kształtów i łączników
 W przypadku zmiany rozmiaru lub koloru kształtu lub przekierowania łącznika nie ma wpływu na Model źródłowy. Jednak po zmianie nazwy kształtu na diagramie lub w Eksploratorze modelu UML odpowiedni element zostanie zmieniony w Eksploratorze modelu UML i we wszystkich innych diagramach, które przedstawiają ten element.

> [!NOTE]
> Istnieje prosty sposób, aby utworzyć nowe elementy przybornika, z których można tworzyć grupy elementów lub elementy z własnymi wyborem właściwości. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md).

 Na poniższej ilustracji przedstawiono sposób zmiany rozmiaru kształtu lub jego nazwy.

 ![Dostosowywanie elementu modelu](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Wbudowane polecenia nie zawierają polecenia służącego do starannego wyrównywania kształtów. Można jednak łatwo utworzyć własne polecenie wyrównania, kopiując kod w przykładzie w obszarze [Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).

 Na poniższej ilustracji przedstawiono sposób dostosowywania trasy i położenia łącznika lub jego etykiet.

 ![Dostosowywanie łącznika](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Aby przenieść jeden koniec łącznika do innego kształtu

1. Wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** i Przenieś koniec.

     \- oraz

   - Kliknij prawym przyciskiem myszy łącznik, a następnie kliknij polecenie **Połącz ponownie**.

2. Kliknij koniec łącznika, który chcesz przenieść.

3. Kliknij kształt, do którego ma zostać przesunięty łącznik.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Aby zmienić kolor lub inne właściwości elementu, relacji lub diagramu

- Kliknij element i Ustaw pola w oknie **Właściwości** .

     Jeśli nie widzisz okna **Właściwości** , kliknij prawym przyciskiem myszy element, a następnie kliknij polecenie **właściwości.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Aby powiększać i pomniejszać na diagramie modelowania

- Naciśnij i przytrzymaj klawisz **Ctrl** podczas obracania kółka myszy.

     \- oraz

- Naciśnij i przytrzymaj **klawisze Ctrl + Shift**, a następnie kliknij lewy lub prawy przycisk myszy.

     \- oraz

- Na pasku narzędzi **projektanci architektury** kliknij znak plus ( **+** ) lub znak minus ( **-** ) lub wybierz poziom powiększenia.

## <a name="searching-in-a-diagram"></a><a name="Searching"></a> Wyszukiwanie w diagramie
 Funkcja szybkiego wyszukiwania znajdzie elementy na diagramie. Należy ustawić wartość **Szukaj w:** do **bieżącego dokumentu**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Aby wyszukać tekst w diagramie modelowania

1. Naciśnij **klawisze CTRL + F**.

     \- oraz

     W menu **Edycja** wskaż polecenie **Znajdź i Zamień**, a następnie kliknij polecenie **szybkie znajdowanie**.

    > [!NOTE]
    > W oknie dialogowym **Znajdź i Zamień** należy pozostawić pole **Szukaj w** ustawione na **bieżący dokument**. Inne opcje nie są obsługiwane.

2. Wpisz tekst, który chcesz znaleźć, a następnie kliknij przycisk **Znajdź dalej**.

    > [!NOTE]
    > Jeśli tekst, który ma zostać znaleziony, znajduje się wewnątrz zwiniętego kształtu, kształt zostanie wyróżniony. Rozwiń kształt, a następnie kliknij ponownie przycisk **Znajdź dalej** .

## <a name="undoing-changes-to-the-model"></a><a name="Undo"></a> Cofanie zmian w modelu
 Można cofnąć i ponownie wykonać zmiany wprowadzone w modelu i diagramach za pomocą poleceń **Cofnij** i **Wykonaj ponownie** w menu **Edycja** .

 **Każdy projekt modelowania ma jeden stos zmian.** Wszystkie zmiany wprowadzone w modelu i diagramy są przechowywane na tym stosie. Stos obejmuje również zmiany ostrości z jednego diagramu na drugi. Polecenie Cofnij Cofa zmiany w tym stosie.

 Załóżmy na przykład, że wykonujesz następujące operacje: wprowadź zmianę do Diagram1; Zmień fokus na diagram 2; Zmień Diagram2. Po cofnięciu zmian, pierwsze cofnięcie spowoduje odwrócenie ostatniej zmiany; Kolejna operacja Cofnij spowoduje zmianę fokusu na diagram 1. natomiast trzecia operacja Cofnij spowoduje odwrócenie zmiany do diagramu 1.

 **Zamknięcie diagramu powoduje obcinanie stosu zmian.** W przypadku zamknięcia diagramu nie można cofnąć zmian, które zostały wykonane na tym diagramie, i nie można cofnąć wcześniejszych zmian w modelu ani na żadnym z jego diagramów.

 **Nie można cofnąć podczas edytowania właściwości.** Podczas edytowania właściwości w okno Właściwości lub w etykiecie na diagramie, można cofnąć tylko zmiany wprowadzone w tej właściwości. Uzupełnij zmiany we właściwości, naciskając klawisz ENTER lub Anuluj je, naciskając klawisz ESC. Następnie będzie można cofnąć zmiany w modelu i diagramach.

 **Zamknięcie diagramu bez zapisywania może nie mieć oczekiwanego wpływu.** Jeśli wprowadzisz pewne zmiany, a następnie zamkniesz diagram bez zapisywania, zmiany zostaną zachowane w modelu. Zalecane jest, aby zamknąć cały model, jeśli chcesz to zrobić bez zapisywania.

## <a name="sharing-elements-between-diagrams"></a><a name="Sharing"></a> Udostępnianie elementów między diagramami
 Określone wystąpienie elementu modelu może pojawić się więcej niż jeden raz w diagramach. Dotyczy to klas, interfejsów, składników, przypadków użycia i aktorów.

 Jest to przydatne, jeśli chcesz wyświetlić różne grupy relacji w różnych diagramach. Na przykład na jednym diagramie można pokazać skojarzenia między klasami klientów i adresów. Na innym diagramie można ponownie pokazać klasę adresów wraz z jej skojarzeniem z obszarem pocztowym.

 Można zmienić właściwości elementu modelu, takie jak jego nazwa, wybierając dowolny z widoków na dowolnym diagramie lub wybierając go w Eksploratorze modelu UML.

 Każdy rodzaj diagramu może zawierać tylko niektóre rodzaje elementów modelu. Na przykład na diagramie składników nie można wyświetlić przypadku użycia. W związku z tym następujące procedury będą działały tylko dla niektórych kombinacji elementu modelu i diagramu.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Aby dodać nowy widok elementu modelu przy użyciu Eksploratora modelu UML

1. Aby otworzyć **Eksploratora modelu UML**, w menu **Architektura** wskaż pozycję **Windows**, a następnie kliknij pozycję **Eksplorator modelu UML**.

2. Przeciągnij element modelu z **Eksploratora modelu UML** do zgodnego diagramu w tym samym projekcie.

     Zostanie wyświetlony kształt zawierający widok elementu modelu, który może być uzupełnieniem widoków na innych diagramach lub na tym samym diagramie.

    > [!NOTE]
    > Efekt jest różny podczas przeciągania klasy lub składnika na diagram sekwencji. W takim przypadku zostanie utworzona nowa linia życia, której typem jest Klasa lub składnik. Aby uzyskać więcej informacji, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Aby dodać nowy widok elementu modelu przy użyciu odwołania wklejania

1. Kliknij prawym przyciskiem myszy istniejący element, a następnie kliknij polecenie **Kopiuj**.

    - Można kopiować kilka elementów jednocześnie. Przytrzymaj wciśnięty klawisz CTRL podczas klikania każdego elementu, kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij polecenie **Kopiuj**.

2. Kliknij prawym przyciskiem myszy pustą część zgodnego diagramu, a następnie kliknij polecenie **Wklej odwołanie**.

     Zostanie wyświetlony inny widok tego samego elementu.

    > [!NOTE]
    > Różni się to od polecenia **Wklej** , które tworzy nowy element w modelu. Aby uzyskać więcej informacji, zobacz [Kopiowanie elementów i grup powiązanych elementów](#Copying).

> [!NOTE]
> W przypadku dodania do widoków diagramu dwóch elementów modelu, które są już połączone przez relację, widok relacji również będzie widoczny na diagramie. Ten widok można usunąć tylko przez usunięcie jednego z elementów z diagramu lub usunięcie relacji z modelu.

## <a name="copying-elements-and-groups-of-related-elements"></a><a name="Copying"></a> Kopiowanie elementów i grup elementów pokrewnych
 Można kopiować i wklejać elementy modelu oraz kopiować i wklejać grupy elementów wraz z relacjami między nimi.

> [!NOTE]
> Polecenia **Wklej** i **Wklej odwołania** mają różne efekty. **Wklejanie** tworzy nowe elementy, których właściwości są podobne do elementów skopiowanych. **Wklej odwołanie** tworzy nowe widoki tych samych elementów.

#### <a name="to-copy-elements-and-their-relationships"></a>Aby skopiować elementy i ich relacje

1. Na diagramie z elementami, które chcesz skopiować, wybierz co najmniej jeden element.

    > [!NOTE]
    > Nie można kopiować relacji poza elementem grupy elementów.

2. W menu **Edycja** kliknij polecenie **Kopiuj**.

3. Jeśli chcesz skopiować elementy do innego diagramu, Utwórz nowy diagram lub Otwórz istniejący diagram.

4. W menu **Edycja** kliknij polecenie **Wklej**.

    - Zostaną wyświetlone kopie elementów wraz z kopiami relacji łączących się między nimi.

    - Każdy nowy element będzie miał nową automatycznie wygenerowaną nazwę.

5. Dostosuj pozycje, nazwy i inne właściwości nowych elementów i relacji.

> [!NOTE]
> Nie można skopiować elementu modelu z jednego modelu do innego, na przykład jeśli istnieją dwa modele w tym samym rozwiązaniu. Można jednak kopiować elementy z jednego diagramu do drugiego.

#### <a name="to-copy-an-entire-diagram"></a>Aby skopiować cały diagram

1. Utwórz nowy diagram.

2. Zaznacz wszystkie elementy na istniejącym diagramie, skopiuj je i wklej je do nowego.

   Nie można replikować diagramu przez kopiowanie i wklejanie w Eksplorator rozwiązań.

## <a name="deleting-a-model-element-or-its-views"></a><a name="Deleting"></a> Usuwanie elementu modelu lub jego widoków
 Niektóre rodzaje elementów, w tym klasyfikatora, można usunąć z diagramu bez usuwania ich z modelu. Klasyfikatory to główne elementy, które są wyświetlane na diagramach klas, diagramach składników i diagramach przypadków użycia. Mogą być wyświetlane na więcej niż jednym diagramie. W przypadku tych typów elementów istnieją dwa oddzielne polecenia: **Usuń z diagramu** i **Usuń z modelu**.

 Z drugiej strony, po usunięciu relacji z diagramu, zawsze jest usuwana z modelu.

> [!NOTE]
> Niektóre rodzaje elementów na diagramie UML mają etykiety. Po wybraniu takich elementów przez rysowanie wokół nich prostokąta można wybrać etykiety, ale nie elementy, które są właścicielami tych etykiet. Usuwanie podzestawu elementów wybranych w ten sposób nie jest obsługiwane. Aby wybrać podzbiór tych elementów, naciśnij i przytrzymaj klawisz **Ctrl** podczas klikania każdego elementu.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Aby usunąć widok klasyfikatora z diagramu

- Kliknij prawym przyciskiem myszy element na diagramie, a następnie kliknij polecenie **Usuń z diagramu**.

  \- oraz

- Kliknij element na diagramie, a następnie naciśnij klawisz **delete** .

  - Ten widok znikający elementu. Jednak element pozostaje w modelu i nadal można go znaleźć w **Eksploratorze modelu UML**. Pozostałe widoki tego samego elementu również pozostają.

  - Każdy Łącznik kończący się na tym kształcie jest usuwany z diagramu, ale relacja, którą reprezentuje, pozostanie w modelu. Relację można zobaczyć w **Eksploratorze modelu UML** w obszarze **relacje**, w obszarze każdy element, który nawiązuje połączenie.

#### <a name="to-delete-an-element-from-the-model"></a>Aby usunąć element z modelu

- Kliknij prawym przyciskiem myszy element w **Eksploratorze modelu UML** lub na diagramie, a następnie kliknij polecenie **Usuń z modelu**.

  - Element zostanie usunięty z każdego diagramu, na którym występuje.

  - Wszystkie relacje kończące się na tym elemencie również są usuwane z modelu.

#### <a name="to-delete-a-relationship-from-the-model"></a>Aby usunąć relację z modelu

- Kliknij prawym przyciskiem myszy relację na diagramie lub w **Eksploratorze modelu UML**, a następnie kliknij polecenie **Usuń z modelu**.

    > [!CAUTION]
    > Nie można usunąć relacji z diagramu bez usuwania go z modelu.

     Relacja jest usuwana z modelu i jest usuwana z każdego diagramu, na którym się znajduje.

## <a name="preparing-a-diagram-for-presentation"></a><a name="presentation"></a> Przygotowywanie diagramu do prezentacji
 Poniższe funkcje ułatwiają narysowanie uwagi do określonych części diagramu, Dodawanie wyjaśnień lub dzielenie diagramu na różne obszary zainteresowania.

- Możesz skopiować dowolną część diagramu do programu Word, PowerPoint lub innego dokumentu. Wybierz odpowiednie kształty i łączniki, kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Kopiuj**.

- Kolor dowolnego kształtu lub łącznika można zmienić. Wybierz co najmniej jeden kształt i zmień właściwość **Color** . Jeśli nie widzisz okna **Właściwości** , naciśnij klawisz **F4**.

- Na diagramach niektórych rodzajów można rysować linie, prostokąty i wielokropek z sekcji **proste kształty** w przyborniku. Te kształty nie są częścią modelu UML.

- Aby dodać etykietę do obszaru, możesz przeciągnąć komentarz z przybornika, a następnie ustawić jego właściwość **transparent** na **true**. Podobnie jak kształty proste, komentarze nie są częścią modelu UML i nie są wyświetlane w Eksploratorze modelu UML.

- Aby dodać uwagi i wyjaśnienia do elementów modelu, można utworzyć komentarze, a następnie połączyć je z elementami.

### <a name="to-export-a-diagram-as-an-image"></a>Aby wyeksportować diagram jako obraz
 Aby uzyskać więcej informacji, zobacz [Eksportowanie diagramów jako obrazów](../modeling/export-diagrams-as-images.md).

## <a name="extending-the-uml-designers"></a><a name="extensions"></a> Rozszerzanie projektantów UML
 Możesz dodać nowe funkcje do narzędzi UML i dostosować do własnych potrzeb notację diagramu. Aby uzyskać więcej informacji, zobacz [rozszerzając modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>Zobacz też
 [Tworzenie projektów modelowania UML i diagramów](../modeling/create-uml-modeling-projects-and-diagrams.md) [analizowanie i architektura](../modeling/analyze-and-model-your-architecture.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)
