---
title: Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41b589526fb1f864c97571db893506bc612893ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660608"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edycja zakodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować właściwości metod testowych i akcji interfejsu użytkownika. Ponadto można użyć mapy formantów interfejsu użytkownika do wyświetlania i edytowania odpowiednich kontrolek.

 **Requirements**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Dlaczego warto to zrobić?
 Korzystanie z edytora kodowanego testu interfejsu użytkownika jest szybsze i wydajniejsze niż edytowanie kodu w kodowanych metodach testowania interfejsu użytkownika za pomocą edytora kodu. Za pomocą edytora kodowanego testu interfejsu użytkownika możesz użyć menu paska narzędzi i skrótów, aby szybko zlokalizować i zmodyfikować wartości właściwości skojarzone z akcjami i kontrolkami interfejsu użytkownika. Na przykład można użyć paska narzędzi edytora kodowanego testu interfejsu użytkownika do wykonania następujących poleceń:

 ![Edito testu interfejsu użytkownika](../test/media/uitesteditor.png "UITestEditor")

1. [Znajdź](../ide/finding-and-replacing-text.md) pomaga zlokalizować akcje i kontrolki interfejsu użytkownika.

2. [Delete](#CodedUITestEditor_DeleteUIActions) usuwa niepożądane akcje interfejsu użytkownika.

3. Zmiana **nazwy** powoduje zmianę nazw dla metod testowych i kontrolek.

4. **Właściwości** otwiera okno właściwości dla wybranego elementu.

5. [Podzielona na nową metodę](#CodedUITestEditor_SplitMethods) pozwala modularyzacji akcje interfejsu użytkownika.

6. [Przenoszenie kodu](#CodedUITestEditor_MoveMethods) dodaje kod niestandardowy do metod testowych.

7. [Wstaw opóźnienie przed](#CodedUITestEditor_InsertDelay) dodaniem pauzy przed akcją interfejsu użytkownika określoną w milisekundach.

8. [Znajdź formant interfejsu użytkownika](#CodedUITestEditor_LocateUIControl) identyfikuje lokalizację kontrolki w interfejsie użytkownika testowanej aplikacji.

9. [Znajdź wszystkie](#CodedUITestEditor_LocateDecendants) ułatwia sprawdzenie właściwości kontrolki i znaczących zmian w kontrolkach aplikacji.

## <a name="how-do-i-do-this"></a>Jak mogę to zrobić?
 W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] otwarcie pliku UIMap. UITest powiązanego z kodowanym testem interfejsu użytkownika w projekcie kodowanego testu interfejsu użytkownika spowoduje automatyczne wyświetlenie kodowanego testu interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. W poniższych procedurach opisano sposób lokalizowania i edytowania metod testowych oraz właściwości akcji interfejsu użytkownika oraz kontrolek przy użyciu paska narzędzi edytora i menu skrótów.

## <a name="open-a-coded-ui-test"></a>Otwieranie kodowanego testu interfejsu użytkownika
 Za pomocą edytora kodowanego testu interfejsu C# użytkownika można wyświetlać i edytować swój graficzny test interfejsu użytkownika oparty na Visual Basicach.

 ![Edytowanie menu kontekstowego za pomocą konstruktora kodowanego testu interfejsu użytkownika](../test/media/editcodeduitest.png "EditCodedUITest")

 W Eksplorator rozwiązań otwórz menu skrótów dla **UIMap. UITest** i wybierz polecenie **Otwórz**. Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować zarejestrowane metody, akcje i odpowiadające im kontrolki w kodowanym teście interfejsu użytkownika.

> [!TIP]
> Po wybraniu akcji interfejsu użytkownika, która znajduje się w metodzie w okienku **akcje interfejsu użytkownika** , odpowiadający jej formant zostanie wyróżniony. Możesz również zmodyfikować akcję interfejsu użytkownika lub właściwości kontrolek.

 Edytor kodowanego testu interfejsu użytkownika *nie jest widoczny* .
Może być używana wersja Visual Studio Enterprise wcześniejsza niż 2012. Edytor kodowanego testu interfejsu użytkownika był również dostępny w programie Visual Studio 2010 Feature Pack 2 z subskrypcją MSDN. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).

## <a name="CodedUITestEditor_EditActionAndControlProperties"></a>Modyfikuj właściwości akcji interfejsu użytkownika i odpowiadające im właściwości kontrolki
 Za pomocą edytora kodowanego testu interfejsu użytkownika można szybko zlokalizować i wyświetlić wszystkie akcje interfejsu użytkownika w metodach testowych. Po wybraniu akcji interfejsu użytkownika w edytorze, odpowiadający jej formant zostanie automatycznie wyróżniony. Analogicznie, jeśli wybierzesz kontrolkę, skojarzone akcje interfejsu użytkownika zostaną wyróżnione. Po wybraniu akcji interfejsu użytkownika lub kontrolki, można łatwo użyć okno Właściwości, aby zmodyfikować właściwości, które odpowiadają.

 ![Właściwości akcji interfejsu użytkownika](../test/media/codeduiedituiaction.png "CodedUIEditUIAction") Edytowanie właściwości akcji interfejsu użytkownika

 Aby zmodyfikować właściwości akcji interfejsu użytkownika, w okienku **Akcja interfejsu użytkownika** rozwiń metodę testową zawierającą akcję interfejsu użytkownika, dla której chcesz edytować właściwości, wybierz akcję interfejsu użytkownika, a następnie zmodyfikuj właściwości przy użyciu okno właściwości.

 Na przykład jeśli serwer jest niedostępny i masz akcję interfejsu użytkownika skojarzoną z przeglądarką sieci Web, która **przechodzi do strony sieci Web "<http://Contoso1/default.aspx’>** , możesz zmienić adres URL na `‘ http://Contoso2/default.aspx’`.

 ![Właściwości kontrolki](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp") Edytowanie właściwości kontrolki

 Modyfikowanie właściwości kontrolki odbywa się w taki sam sposób, jak akcje interfejsu użytkownika. W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę, którą chcesz edytować i zmodyfikować jej właściwości przy użyciu okno właściwości.

 Na przykład deweloper mógł zmienić właściwość **(ID)** w kontrolce Button w kodzie źródłowym testowanej aplikacji z "idSubmit" na "idLogin". Po zmianie właściwości **(ID)** w aplikacji kodowany test interfejsu użytkownika nie będzie mógł zlokalizować kontrolki przycisku i zakończy się niepowodzeniem. W takim przypadku tester może otworzyć kolekcję **Właściwości wyszukiwania** i zmienić właściwość **ID** tak, aby odpowiadała nowej wartości używanej przez dewelopera w aplikacji. Tester może również zmienić **przyjazną** wartość właściwości Nazwa z "Prześlij" do "login". Wprowadzając tę zmianę, skojarzona akcja interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika zostaje zaktualizowana z "Wybierz przycisk" Prześlij "do" Wybierz "przycisk" Login' ".

 Po zakończeniu modyfikacji Zapisz zmiany w pliku UIMap. Designer, wybierając pozycję **Zapisz** na pasku narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *Co jeszcze mam wiedzieć?*
 **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Jeśli okno Właściwości nie jest wyświetlana, naciśnij i przytrzymaj klawisz **Alt** podczas naciskania klawisza **Enter**lub naciśnij klawisz **F4**.

- ![Porada](../test/media/tip.png "Porada") Aby cofnąć wprowadzone zmiany właściwości, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisze Ctrl + Z.

- ![Porada](../test/media/tip.png "Porada") Aby otworzyć narzędzie Znajdź i Zamień w programie Visual Studio, można użyć przycisku **Znajdź** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Następnie można użyć kontrolki Znajdź, aby zlokalizować akcję interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. Na przykład możesz spróbować znaleźć przycisk "kliknij" Login' ". Może to być przydatne w przypadku dużych testów. Należy pamiętać, że nie można użyć funkcji Replace w narzędziu Znajdź i Zamień w edytorze kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz Znajdowanie formantu przy [znajdowaniu i zamienianiu tekstu](../ide/finding-and-replacing-text.md).

- ![Porada](../test/media/tip.png "Porada") Czasami może być trudne Wizualizacja, gdzie kontrolki znajdują się w interfejsie użytkownika testowanej aplikacji. Jedną z możliwości edytora kodowanego testu interfejsu użytkownika jest możliwość wybrania kontrolki wymienionej na mapie formantów interfejsu użytkownika i wyświetlenia jej lokalizacji w testowanej aplikacji. [!INCLUDE[crdefault](../includes/crdefault-md.md)][lokalizowanie kontrolki interfejsu użytkownika w testowanej aplikacji](#CodedUITestEditor_LocateUIControl) znajdującej się w dalszej części tego tematu.

- ![Porada](../test/media/tip.png "Porada") Może być konieczne rozszerzenie kontrolki kontenera zawierającej kontrolkę, którą chcesz edytować. [!INCLUDE[crdefault](../includes/crdefault-md.md)][lokalizowanie kontrolki i jej elementów podrzędnych](#CodedUITestEditor_LocateDecendants) znajdujących się w dalszej części tego tematu.

## <a name="CodedUITestEditor_DeleteUIActions"></a>Usuń niepożądane akcje interfejsu użytkownika
 Można łatwo usunąć niepożądane akcje interfejsu użytkownika w kodowanym teście interfejsu użytkownika.

 ![Usuń akcję interfejsu użytkownika](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")

 W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która zawiera akcję interfejsu użytkownika, którą chcesz usunąć. Otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz polecenie **Usuń**.

## <a name="CodedUITestEditor_SplitMethods"></a>Podziel metodę testową na dwie oddzielne metody
 Można podzielić metodę testową, aby udoskonalić lub modularyzacji akcje interfejsu użytkownika. Na przykład, test może mieć pojedynczą metodę testową z akcjami interfejsu użytkownika w dwóch kontrolkach kontenera. Akcje interfejsu użytkownika mogą być lepiej modularne w dwóch metodach odpowiadających jednemu kontenerowi.

 ![Splt metodę testową](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![Dwie metody testowe](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która ma zostać podzielona na dwie oddzielne metody, a następnie wybierz akcję interfejsu użytkownika, w której chcesz rozpocząć nową metodę testową. Otwórz menu skrótów dla akcji interfejsu użytkownika, a następnie wybierz polecenie **Podziel na nową metodę**lub wybierz przycisk **Podziel na nową metodę** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Nowa metoda testowa zostanie wyświetlona w okienku Akcje interfejsu użytkownika. Zawiera akcje interfejsu użytkownika, rozpoczynając od akcji, w której został określony podział.

 Po zakończeniu dzielenia metody Zapisz zmiany w pliku UIMap. Designer, wybierając pozycję **Zapisz** na pasku narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *Co jeszcze mam wiedzieć?*
 **Ważne problemy**

- Ostrzeżenie ![ikony](../test/media/caution.gif "Ostrzeżenie") **ostrzeżenia:** w przypadku podziału metody należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, która ma zostać utworzona, jeśli nadal chcesz, aby te akcje interfejsu użytkownika zostały uwzględnione. Podczas dzielenia metody zostanie wyświetlone okno dialogowe Microsoft Visual Studio. Ostrzega o tym, że musisz zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, którą chcesz utworzyć. Wybierz opcję **tak**.

  **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Aby cofnąć podział, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisze Ctrl + Z.

- ![Porada](../test/media/tip.png "Porada") Nową metodę można zmienić. Wybierz go w okienku Akcje interfejsu użytkownika i wybierz przycisk **Zmień nazwę** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.

   —lub—

   Otwórz menu skrótów dla nowej metody testowej i wybierz polecenie **Zmień nazwę**.

   Pojawi się okno dialogowe programu Microsoft Visual Studio. Ostrzega o tym, że należy zmodyfikować kod odwołujący się do tej metody. Wybierz opcję **tak**.

## <a name="CodedUITestEditor_MoveMethods"></a>Przenieś metodę testową do pliku UIMap, aby ułatwić dostosowanie
 Jeśli określisz, że jedna z metod testowych w kodowanym teście interfejsu użytkownika wymaga kodu niestandardowego, musisz przenieść ją do pliku UIMap.cs lub UIMap. vb. W przeciwnym razie kod zostanie nadpisany po każdym ponownym skompilowaniu kodowanego testu interfejsu użytkownika. Jeśli nie przeniesiesz metody, kod niestandardowy zostanie nadpisany za każdym razem, gdy test zostanie ponownie skompilowany.

 W okienku **Akcja interfejsu użytkownika** wybierz metodę testową, która ma zostać przeniesiona do pliku UIMap.cs lub UIMap. vb, aby ułatwić niestandardowe funkcje kodu, które nie zostaną zastąpione podczas ponownej kompilacji kodu testowego. Następnie wybierz przycisk **Przenieś kod** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika lub Otwórz menu skrótów dla metody testowej i wybierz polecenie **Przenieś kod**. Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, Otwórz plik UIMap.cs lub UIMap. vb z Eksplorator rozwiązań.

 Po zakończeniu przeniesienia metody Zapisz zmiany w pliku UIMap. Designer, wybierając pozycję **Zapisz** na pasku narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *Co jeszcze mam wiedzieć?*
 **Ważne problemy**

- Ostrzeżenie ![ikony](../test/media/caution.gif "Ostrzeżenie") **ostrzeżenia:** po przeniesieniu metody nie można już edytować jej przy użyciu edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Podczas przenoszenia metody wyświetlane jest okno dialogowe Microsoft Visual Studio. Ostrzega o tym, że metoda zostanie przeniesiona z pliku UIMap. UITest do pliku UIMap.cs lub UIMap. vb i nie będzie już można edytować metody przy użyciu edytora kodowanego testu interfejsu użytkownika. Wybierz opcję **tak**.

  **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Aby cofnąć przeniesienie, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisze Ctrl + Z. Należy jednak ręcznie usunąć kod z pliku UIMap.cs lub UIMap. vb.

## <a name="CodedUITestEditor_LocateUIControl"></a>Lokalizowanie kontrolki interfejsu użytkownika w testowanej aplikacji
 Czasami może być trudne Wizualizacja, gdzie kontrolki znajdują się w interfejsie użytkownika testowanej aplikacji. Jedną z możliwości edytora kodowanego testu interfejsu użytkownika jest możliwość wybrania kontrolki wymienionej na mapie formantów interfejsu użytkownika i wyświetlenia jej lokalizacji w testowanej aplikacji. Za pomocą funkcji **lokalizowania kontrolki interfejsu użytkownika** w testowanej aplikacji można także sprawdzić modyfikacje właściwości wyszukiwania dokonane w formancie.

 ![Lokalizowanie kontrolki interfejsu użytkownika](../test/media/codeduilocatecontrol.png "CodedUILocateControl")

 ![Kontrolka znajdująca się w testowanej aplikacji](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę, którą chcesz zlokalizować w aplikacji skojarzonej z testem. Następnie otwórz menu skrótów dla kontrolki, a następnie wybierz pozycję **Zlokalizuj formant interfejsu użytkownika**. W testowanej aplikacji kontrolka jest oznaczona niebieską krawędzią.

 *Co jeszcze mam wiedzieć?*
 **Ważne problemy**

- Ostrzeżenie ![ikony](../test/media/caution.gif "Ostrzeżenie") **ostrzeżenia:** przed ZLOKALIZOWANIEM kontrolki interfejsu użytkownika Sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

  **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Alternatywnie możesz użyć opcji **Znajdź wszystko** , aby sprawdzić, czy wszystkie kontrolki w kontenerze mogą być prawidłowo zlokalizowane. Ta opcja jest opisana w następnej sekcji.

## <a name="CodedUITestEditor_LocateDecendants"></a>Lokalizowanie formantu i jego elementów podrzędnych
 Można sprawdzić, czy wszystkie kontrolki w kontenerze mogą być prawidłowo zlokalizowane w interfejsie użytkownika testowanej aplikacji. Może to pomóc w sprawdzeniu zmian właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto, jeśli wprowadzono znaczące zmiany w interfejsie użytkownika testowanej aplikacji, można sprawdzić, czy istniejące właściwości wyszukiwania kontrolki są nadal poprawne.

 ![Lokalizowanie wszystkich formantów podrzędnych](../test/media/codeduilocateall.png "CodedUILocateAll")

 ![Wszystkie kontrolki zlokalizowane](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę kontenera, którą chcesz zlokalizować, i Wyświetl wszystkie obiekty podrzędne. Następnie otwórz menu skrótów dla kontrolki i wybierz pozycję **Znajdź wszystkie**. Formant kontenera i wszystkie jego elementy podrzędne są oznaczone w edytorze kodowanego testu interfejsu użytkownika z zielonym znacznikiem wyboru lub czerwoną literą "X". Znaczniki te informują o tym, czy kontrolki zostały pomyślnie umieszczone w testowanej aplikacji.

 *Co jeszcze mam wiedzieć?*
 **Ważne problemy**

- Ostrzeżenie ![ikony](../test/media/caution.gif "Ostrzeżenie") **ostrzeżenia:** przed zlokalizowaniem formantów interfejsu użytkownika Sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

## <a name="CodedUITestEditor_InsertDelay"></a>Wstawianie opóźnienia przed akcją interfejsu użytkownika
 Czasami możesz chcieć, aby test czekał na pewne zdarzenia, takie jak okno, które ma zostać wyświetlone, pasek postępu, który znika i tak dalej. Za pomocą edytora kodowanego testu interfejsu użytkownika można to osiągnąć, wstawiając opóźnienie przed akcją interfejsu użytkownika. Można określić, ile sekund ma mieć opóźnienie.

 ![Wstaw opóźnienie przed akcją interfejsu użytkownika](../test/media/codeduidelay.png "CodedUIDelay")

 ![Opóźnienie dodane z 5 sekund](../test/media/codeduidealy2.png "CodedUIDealy2")

 W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która zawiera akcję interfejsu użytkownika, do której chcesz wstawić opóźnienie. Wybierz akcję interfejsu użytkownika. Następnie otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz polecenie **Wstaw opóźnienie przed**. Opóźnienie jest wstawiane i wyróżniane przed wybraną akcją interfejsu użytkownika o następującym tekście: **poczekaj 1 sekund na opóźnienie użytkownika między akcjami**. W okno Właściwości zmień wartość właściwości **opóźnienie** na żądaną liczbę milisekund.

 Po wstawieniu opóźnienia Zapisz zmiany w pliku UIMap. Designer, wybierając pozycję **Zapisz** na pasku narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *Co jeszcze mam wiedzieć?*
 **Uwagi**

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Aby upewnić się, że określony formant jest dostępny przed akcją interfejsu użytkownika, należy rozważyć dodanie niestandardowego kodu do metody testowej przy użyciu odpowiedniej metody UITestControl. WaitForControlXXX (). [!INCLUDE[crdefault](../includes/crdefault-md.md)][tworzenia kodowanych testów interfejsu użytkownika Zaczekaj na określone zdarzenia podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

  **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Jeśli okno Właściwości nie jest wyświetlana, naciśnij i przytrzymaj klawisz Alt podczas naciskania klawisza Enter lub alternatywnie naciśnij klawisz F4.

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)

### <a name="faq"></a>Najczęściej zadawane pytania
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](http://go.microsoft.com/fwlink/?LinkID=230576)

 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 2](http://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Forum
 [Testowanie automatyzacji interfejsu użytkownika programu Visual Studio (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [Tworzenie KODOWANYch testów interfejsu](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) użytkownika tworzenie kodowanego [testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md) , [generującego kodowany test interfejsu użytkownika z istniejącego przewodnika rejestrowania akcji](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika ](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
