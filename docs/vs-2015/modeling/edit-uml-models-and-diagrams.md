---
title: Edytowanie modeli i diagramów UML | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3cc16133911cf4b49af983aabb4b7b60405c956c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777450"
---
# <a name="edit-uml-models-and-diagrams"></a>Edytowanie modeli i diagramów UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć i edytować modelu UML za pomocą widoków, dostarczone przez różne rodzaje diagramów. Dostarczając z różnych perspektyw w systemie, te diagramy pomaga zrozumieć i różnych aspektów projektu i wymagania. Program Visual Studio udostępnia szablony dla 5 najbardziej często używanych typów diagramu UML.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 W tym temacie opisano techniki edytowania modelu, które są wspólne między typami innym diagramie. Aby uzyskać więcej informacji, które są specyficzne dla określonych rodzajów diagramy, zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>W tym temacie  
  
-   [Diagramy UML są widokami modelu UML](#Views)  
  
-   [Tworzenie diagramów modelowania UML](#Creating)  
  
-   [Rysowanie diagramów modelowania UML](#Drawing)  
  
-   [Edytowanie kształtów i łączników](#Editing)  
  
-   [Cofanie zmian do modelu](#Undo)  
  
-   [Udostępnianie elementów między diagramów](#Sharing)  
  
-   [Kopiowanie elementów i grup powiązanych elementów](#Copying)  
  
-   [Usuwanie elementu modelu lub jego widoków](#Deleting)  
  
-   [Wyszukiwanie tekstu w diagramie](#Searching)  
  
-   [Trwa przygotowywanie diagramu, aby obejrzeć prezentację](#presentation)  
  
-   [Rozszerzenia projektantów UML](#extensions)  
  
##  <a name="Views"></a> Diagramy UML są widokami modelu UML  
 Można tworzyć i używać diagramów UML tylko w projektach modelowania. Aby uzyskać więcej informacji na temat tworzenia diagramów i projektów, zobacz [UML tworzenie projektów i diagramów modelowania](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Projekt modelowania zawiera pojedynczego modelu UML. Każdy diagram UML w projekcie jest widokiem modelu UML.  
  
-   Możesz zobaczyć modelu w **Eksploratora modelu UML**. Na **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
-   Każdy kształt na diagramie jest widoku elementu w modelu. Możesz umieścić nowy kształt na diagramie, powoduje utworzenie nowego elementu w modelu.  
  
-   Gdy zapiszesz dowolnego diagramu programu Visual Studio zapisuje cały model, wszystkie jego diagramów i modelowania pliku projektu.  
  
##  <a name="Creating"></a> Tworzenie diagramów modelowania UML  
  
1. Na **architektury** menu w programie Visual Studio, kliknij **nowe UML lub diagramu warstwowego**.  
  
2. Wybierz, a nazwa diagramu.  
  
3. W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania lub **Utwórz nowy projekt modelowania**.  
  
   > [!NOTE]
   >  Na diagramie modelowania, musi istnieć w projekcie modelowania.  
  
   Diagram można również dodać do istniejącego projektu modelowania w Eksploratorze rozwiązań. Kliknij prawym przyciskiem myszy projekt modelowania, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Aby utworzyć pusty projekt modelowania UML  
  
- Na **pliku** menu, wskaż **nowy**, kliknij przycisk **projektu**, a następnie w **nowy projekt** okno dialogowe, kliknij dwukrotnie **modelowania Projekty**.  
  
  Aby uzyskać więcej informacji o sposobie zarządzania projektów modelowania, zobacz [UML tworzenie projektów i diagramów modelowania](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> Rysowanie diagramów modelowania UML  
 Kolekcja elementów modelu połączonego przez zastosowanie relacji są wyświetlane na diagramie modelowania. Każdy element jest wyświetlana jako kształt, a każda relacja jest wyświetlana jako łącznik między dwoma kształtami.  
  
 Istnieją dwa rodzaje narzędzia: jeden dla elementów, a drugi dla relacji. Na przykład w diagramie klas UML przybornika **klasy** jest narzędziem elementu i **skojarzenia** to narzędzie relacji.  
  
> [!NOTE]
>  Aby uzyskać informacje, które są specyficzne dla typów określonego diagram zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Aby utworzyć elementów i relacji na diagramie modelowania UML  
  
1. Aby utworzyć element modelu, kliknij narzędzie elementu w przyborniku, a następnie kliknij przycisk diagram, w której ma się pojawić. Po utworzeniu elementu dostosować jego rozmiar i kształt, przeciągając uchwyty.  
  
    W niektórych przypadkach można umieścić nowy element wewnątrz innego elementu. Na przykład na diagramie klas UML, można umieścić klasy w pakiecie.  
  
   > [!NOTE]
   >  Jeśli przybornik jest niewidoczny, kliknij przycisk **przybornika** na **widoku** menu.  
  
2. Można utworzyć relacji, kliknij narzędzie relację, kliknij element, którego relacji, aby rozpocząć, a następnie kliknij element, gdzie ma się zakończyć.  
  
    Różne typy relacji mogą początku ani na końcu na różnych typach elementów. Na diagramie klas UML, relacja skojarzenia nie może na przykład uruchomić ani kończyć się w elemencie komentarz.  
  
   > [!NOTE]
   >  Aby użyć tego samego narzędzia kilka razy, kliknij dwukrotnie narzędzie. Po zakończeniu kliknij przycisk **wskaźnik** narzędzia.  
  
   Na niektóre rodzaje diagramów można rysować kształty proste. Kształty te nie są częścią modelu, ale można je zwrócić uwagę czytelnika na części diagramu lub podziel go na różnych obszarach.  
  
##  <a name="Editing"></a> Edytowanie kształtów i łączników  
 Podczas zmiany rozmiaru lub kolor kształtu lub przekierowywanie łącznika nie ma żadnego wpływu na odpowiedni model. Jednak po użytkownik zmieni nazwę kształtu na diagramie lub w Eksploratorze modelu UML, odpowiadający mu element jest zmieniana w Eksploratorze modelu UML i inne diagramy, które są dostępne z tego elementu.  
  
> [!NOTE]
>  Brak prosty sposób, aby nowe elementy paska narzędzi, z których możesz utworzyć grupy elementów lub elementów z wybranym właściwości. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 Poniższa ilustracja pokazuje, jak zmienić rozmiar kształtu lub jego nazwę.  
  
 ![Dostosowywanie elementu modelu](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Wbudowane polecenia nie zawierają polecenia starannego wyrównywania kształtów. Jednak łatwo można utworzyć polecenia wyrównanie, kopiując kod w przykładzie w [wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).  
  
 Na poniższej ilustracji przedstawiono, jak dostosować trasy i położenia łącznika lub jej etykiet.  
  
 ![Dostosowywanie łącznika](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Aby przenieść jednym końcu łącznika do innego kształtu  
  
1. Wykonaj jedną z następujących czynności:  
  
   - Naciśnij klawisz **CTRL** i Przenieś na koniec.  
  
     \- lub —  
  
   - Kliknij prawym przyciskiem myszy łącznik, a następnie kliknij przycisk **Reconnect**.  
  
2. Kliknij na końcu łącznika którego chcesz przenieść.  
  
3. Kliknij kształt, którego chcesz, aby łącznik aby przejść do.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Zmień kolor lub innych właściwości elementu, relacji lub diagram  
  
-   Kliknij element, a następnie ustaw pola w **właściwości** okna.  
  
     Jeśli nie widzisz **właściwości** , kliknij prawym przyciskiem myszy element, a następnie kliknij przycisk **właściwości.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Można powiększać i pomniejszać na diagramie modelowania  
  
-   Naciśnij i przytrzymaj klawisz **CTRL** klucza podczas obrót kółkiem myszy.  
  
     \- lub —  
  
-   Naciśnij i przytrzymaj klawisz **CTRL + SHIFT**, a następnie kliknij przycisk myszy w lewo lub w prawo.  
  
     \- lub —  
  
-   Na **projektanci architektury** narzędzi, kliknij znak plus (**+**) lub znak minus (**-**), lub wybierz poziom powiększenia.  
  
##  <a name="Searching"></a> Wyszukiwanie w diagramie  
 Funkcja szybkiego wyszukiwania zawiera elementy na diagramie. Należy ustawić **przeszukania:** do **bieżący dokument**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Aby wyszukać tekst w diagramie modelowania  
  
1.  Naciśnij klawisz **klawisze CTRL + F**.  
  
     \- lub —  
  
     Na **Edytuj** menu wskaż **Znajdź i Zamień**, a następnie kliknij przycisk **szybkie znajdowanie**.  
  
    > [!NOTE]
    >  W **Znajdź i Zamień** okno dialogowe, musi zostawić **przeszukania** pola **bieżący dokument**. Inne opcje nie są obsługiwane.  
  
2.  Wpisz tekst, który chcesz odnaleźć, a następnie kliknij przycisk **Znajdź następny**.  
  
    > [!NOTE]
    >  Jeśli tekst, który ma zostać odnaleziona znajduje się wewnątrz zwiniętego kształtu, kształt zostanie wyróżniona. Rozwiń kształt, a następnie kliknij przycisk **Znajdź następny** ponownie.  
  
##  <a name="Undo"></a> Cofanie zmian do modelu  
 Można cofnąć i wykonaj ponownie zmiany wprowadzone do modelu i diagramy za pomocą **Cofnij** i **wykonaj ponownie** polecenia na **Edytuj** menu.  
  
 **Każdy projekt modelowania zawiera pojedynczy stosu zmian.** Wszystkie zmiany wprowadzone do modelu i diagramy są przechowywane na tego stosu. Stos zawiera również zmiany fokus z jednym diagramie. Polecenie Undo odwraca zmiany dla tego stosu.  
  
 Na przykład załóżmy, że wykonywać te operacje: Wprowadź zmianę Diagram1; Zmień fokus na diagramie 2; Zmień Diagram2. Po cofnięciu zmian pierwszy cofania wycofasz ostatnią zmianę; dalej cofanie będzie przenieść fokus z diagramu 1; i trzeci cofania wycofasz zmiany 1 diagramu.  
  
 **Zamykanie diagramu obcina stosu zmiany.** Jeśli zamkniesz diagramu, nie można cofnąć zmiany, które były wykonywane na tym diagramie i wcześniejszych zmian do modelu lub dowolnego z jego diagramów nie można cofnąć.  
  
 **Nie można cofnąć podczas edytowania właściwości.** Podczas edytowania właściwości w oknie dialogowym właściwości lub w etykiecie na diagramie tylko można cofnąć zmiany wprowadzone w tej właściwości. Wykonaj zmiany we właściwości, naciskając klawisz ENTER lub Anuluj ją, naciskając klawisz ESC. Następnie można cofnąć zmiany w modelu i diagramy.  
  
 **Zamykanie diagramu bez zapisywania może nie mieć efektu, których oczekujesz.** Jeśli wprowadzić pewne zmiany, a następnie zamknij diagram bez zapisywania go, zmiany zostaną zachowane nadal w modelu. Zalecane jest, aby zamknąć cały model, jeśli chcesz to zrobić bez zapisywania go.  
  
##  <a name="Sharing"></a> Udostępnianie elementów między diagramów  
 Można wprowadzić konkretne wystąpienie elementu modelu występować więcej niż raz na diagramach. Dotyczy to klasy, interfejsy, składników, przypadków użycia i aktorów.  
  
 Jest to przydatne, jeśli chcesz wyświetlić różne grupy relacje w różnych diagramach. Na przykład na jednym diagramie można pokazać skojarzenia między klasami klientów i adresu. Na innym diagramie klasy adresów można pokazać ponownie, z jego skojarzenia do obszaru pocztowy.  
  
 Właściwości elementu modelu, takie jak jego nazwa, można zmienić, wybierając dowolną opinię na dowolny diagram lub wybierając go w Eksploratorze modelu UML.  
  
 Każdy rodzaj elementu diagramu można wyświetlić tylko niektóre rodzaje elementu modelu. Na przykład nie można wyświetlić przypadek użycia na diagramie składników. W związku z tym następujące procedury będzie działać tylko w przypadku niektórych kombinacji element modelu i diagram.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Aby dodać nowy widok elementu modelu przy użyciu Eksploratora modelu UML  
  
1.  Aby otworzyć **Eksploratora modelu UML**na **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
2.  Przeciągnij element modelu z **Eksploratora modelu UML** zgodne diagram w tym samym projekcie.  
  
     Kształt z warunkiem, że zostanie wyświetlony widok elementu modelu, które mogą być oprócz widoków na inne diagramy lub ten sam schemat.  
  
    > [!NOTE]
    >  Efekt różni się po przeciągnięciu klasy lub składnik na diagramie sekwencji. W takim przypadku nowy linii życia jest tworzony, którego typem jest tej klasy lub składnika. Aby uzyskać więcej informacji, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Aby dodać nowy widok elementu modelu przy użyciu Wklej odwołanie  
  
1.  Kliknij prawym przyciskiem myszy istniejącego elementu, a następnie kliknij przycisk **kopiowania**.  
  
    -   Skopiuj z kilku elementów, w tym samym czasie. Przytrzymaj klawisz CTRL podczas kliknij każdy element, kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij **kopiowania**.  
  
2.  Kliknij prawym przyciskiem myszy pustą część diagramu zgodne, a następnie kliknij przycisk **Wklej odwołanie**.  
  
     Zostanie wyświetlony inny widok tego samego elementu.  
  
    > [!NOTE]
    >  To różni się od **Wklej** polecenia, które tworzy nowy element w modelu. Aby uzyskać więcej informacji, zobacz [kopiowanie elementów i grupuje pokrewne elementy](#Copying).  
  
> [!NOTE]
>  Jeśli dodasz do widoków diagramu, dwa elementy modelu, które są już połączone poprzez relację, widok relacji również pojawi się na diagramie. W tym widoku można usunąć tylko przez usunięcie jednego z elementów z diagramu lub przez usunięcie zależności od modelu.  
  
##  <a name="Copying"></a> Kopiowanie elementów i grup powiązanych elementów  
 Można skopiować i wkleić elementy modelu, a także można skopiować i wkleić grup elementów wraz z relacji między nimi.  
  
> [!NOTE]
>  **Wklej** i **Wklej odwołanie** polecenia mają różne efekty. **Wklej** tworzy nowe elementy, których właściwości są podobne do tych skopiowane elementy. **Wklej odwołanie** tworzy nowe widoki te same elementy.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Aby skopiować elementy i ich relacji  
  
1.  Na diagramie z elementami, które chcesz skopiować zaznacz jeden lub więcej elementów.  
  
    > [!NOTE]
    >  Nie można skopiować relacje z wyjątkiem jako część grupy elementów.  
  
2.  Na **Edytuj** menu, kliknij przycisk **kopiowania**.  
  
3.  Jeśli chcesz skopiować elementy do innego diagramu, Utwórz nowy diagram, lub Otwórz istniejący diagram.  
  
4.  Na **Edytuj** menu, kliknij przycisk **Wklej**.  
  
    -   Kopiuje elementy są wyświetlane wraz z kopiuje wszystkie relacje, które łączą się między nimi.  
  
    -   Każdy nowy element ma nowy automatycznie wygenerowaną nazwę.  
  
5.  Dostosuj stanowiska, nazwy i inne właściwości nowych elementów i relacji.  
  
> [!NOTE]
>  Nie można skopiować elementu modelu z jednego modelu, do innego, na przykład jeśli masz dwa modele w tym samym rozwiązaniu. Jednak elementy z jednym diagramie można skopiować do innego.  
  
#### <a name="to-copy-an-entire-diagram"></a>Aby skopiować cały diagram  
  
1. Utwórz nowy diagram.  
  
2. Wybierz wszystkie elementy na diagramie istniejących, skopiuj je i wklej je do nowego.  
  
   Nie można replikować diagramu przez kopiowanie i wklejanie w Eksploratorze rozwiązań.  
  
##  <a name="Deleting"></a> Usuwanie elementu modelu lub jego widoków  
 Niektóre rodzaje elementów, w szczególności klasyfikatorów, można usunąć z diagramu bez ich usuwania z modelu. Klasyfikatorów są elementy główne, które są wyświetlane na diagramach, diagramy składników i diagramy przypadków użycia. Może się pojawić na więcej niż jednym diagramie. Dla tych typów elementów istnieją dwa osobne polecenia: **Usuń z diagramu** i **usunięte z modelu**.  
  
 Z drugiej strony podczas usuwania relacji z diagramu zawsze usuwasz je z modelu.  
  
> [!NOTE]
>  Niektóre rodzaje elementów na diagramie UML ma etykiety. Po wybraniu takie elementy za pomocą rysowania prostokąt wokół nich jest możliwe do wybrania etykiety, ale nie elementy, które są właścicielami tych etykiet. Usuwanie podzbiór elementów, które są wybrane w ten sposób nie jest obsługiwane. Aby wybrać podzbiór tych elementów, naciśnij i przytrzymaj klawisz **CTRL** klucza podczas klikania każdego elementu.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Aby usunąć widok klasyfikatora z diagramu  
  
- Kliknij prawym przyciskiem myszy element na diagramie, a następnie kliknij przycisk **Usuń z diagramu**.  
  
  \- lub —  
  
- Kliknij element na diagramie, a następnie naciśnij klawisz **Usuń** klucza.  
  
  -   Ten widok elementu znika. Jednak element pozostaje w modelu i nadal można znaleźć w **Eksploratora modelu UML**. Inne widoki, tego samego elementu też pozostać.  
  
  -   Każdy łącznik, który kończy się na ten kształt zostanie usunięty z diagramu, ale relacji reprezentuje pozostaje w modelu. Możesz zobaczyć relację w **Eksploratora modelu UML** w obszarze **relacje**, w ramach każdego elementu, który nawiązuje połączenie.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Aby usunąć element z modelu  
  
-   Albo kliknij prawym przyciskiem myszy element w **Eksploratora modelu UML** lub na diagram, a następnie kliknij przycisk **usunięte z modelu**.  
  
    -   Element został usunięty z każdy diagram, na którym jest wyświetlana.  
  
    -   Każda relacja, która kończy się na ten element jest również usunięte z modelu.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Aby usunąć relację z modelu  
  
-   Kliknij prawym przyciskiem myszy relację na diagramie lub w **Eksploratora modelu UML**, a następnie kliknij przycisk **usunięte z modelu**.  
  
    > [!CAUTION]
    >  Nie można usunąć relacji z diagramu, bez usuwania go z modelu.  
  
     Relacja zostanie usunięta z modelu i zostanie usunięta z każdy diagram, na którym jest wyświetlana.  
  
##  <a name="presentation"></a> Trwa przygotowywanie diagramu, aby obejrzeć prezentację  
 Następujące funkcje ułatwiają zwrócić uwagę czytelnika na określoną części diagramu, Dodaj wyjaśnienie lub Podziel diagramu na różne obszary zainteresowania.  
  
-   Skopiuj z jakiejkolwiek części diagramu, do programu Word, PowerPoint lub innego dokumentu. Wybierz kształty i łączniki, ma, kliknij prawym przyciskiem myszy, a następnie kliknij przycisk **kopiowania**.  
  
-   Można zmienić kolor dowolnego kształtu lub połączenia. Wybierz jeden lub więcej kształtów i zmień **kolor** właściwości. Jeśli nie widzisz **właściwości** naciśnij klawisze **F4**.  
  
-   Na diagramach niektórych typów, można narysować linie, prostokąty i wielokropek z **kształty proste** sekcji przybornika. Te kształty nie stanowią części modelu UML.  
  
-   Aby dodać etykietę obszar, przeciągnij komentarz z przybornika, a następnie ustaw jego **przezroczysty** właściwości **True**. Podobnie jak kształty proste komentarze nie stanowią części modelu UML i nie są wyświetlane w Eksploratorze modelu UML.  
  
-   Aby dodać informacje i wyjaśnienia do elementów modelu, można tworzyć komentarze i połączyć je z elementami.  
  
-   Aby wyrównać starannego wiersza lub kolumny kształtów na diagramie, można zainstalować polecenia Wyrównaj kształty. Jest on dostępny jako przykładowe rozszerzenie UML:  [UML: Polecenie połączenia kształtów](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Aby wyeksportować diagram jako obraz  
 Aby uzyskać więcej informacji, zobacz [Eksportowanie diagramów jako obrazów](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> Rozszerzenia projektantów UML  
 Można dodawać nowe funkcje do narzędzi UML i dostosowania notacji diagram do własnych potrzeb. Aby uzyskać więcej informacji, zobacz [modeli i diagramów UML rozszerzyć](../modeling/extend-uml-models-and-diagrams.md).  
  
 Brak dostępnych kilka rozszerzeń próbki. Można po prostu zainstalować i używać ich oraz umożliwia ich kod źródłowy na podstawie własnych rozszerzeń. Przykłady obejmują:  
  
|||  
|-|-|  
|[Połączenia kształtów](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Polecenia menu, który pomoże Ci uporządkować dane diagramu.|  
|[Link do witryny docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Połączyć dowolny element UML nagłówki programu Word, slajdy programu PowerPoint, pliki dowolnego typu, diagramy UML lub innych elementów UML. Łącze jest możliwe poprzez przeciąganie. Później można kliknąć dwukrotnie element, aby zobaczyć połączony element. Na przykład można połączyć przypadki użycia specyfikacji programu Word lub diagramów aktywności szczegółowe i akcje do scenorysu slajdów.|  
|[Szybka wejścia](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Szybko utworzyć model przy użyciu wprowadzania tekstu. Przydatne w przypadku przechwytywania pomysłów spotkania.|  
|[Kolor według stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Kolory klasy zgodnie ze stereotypów. Możesz łatwo rozszerzyć kodu do pracy własne stereotypów.|  
|[Modelowanie domeny](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Wygodne domyślnej dla modeli biznesowych. Skojarzenia są wyświetlane bez strzałek domyślnie, a operacje są niewidoczne w klasach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektów modelowania UML i diagramów](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
