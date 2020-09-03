---
title: Edytowanie kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c2fcf3d8807e9095abc9546e8bf1e39aecb8ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288731"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika

Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować właściwości metod testowych i akcji interfejsu użytkownika. Ponadto można użyć mapy formantów interfejsu użytkownika do wyświetlania i edytowania odpowiednich kontrolek.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise
- Składnik kodowanego testu interfejsu użytkownika

## <a name="features-of-the-coded-ui-test-editor"></a>Funkcje edytora kodowanego testu interfejsu użytkownika

Korzystanie z edytora kodowanego testu interfejsu użytkownika jest szybsze i wydajniejsze niż edytowanie kodu w kodowanych metodach testowania interfejsu użytkownika za pomocą edytora kodu. Za pomocą edytora kodowanego testu interfejsu użytkownika możesz użyć menu paska narzędzi i skrótów, aby szybko zlokalizować i zmodyfikować wartości właściwości skojarzone z akcjami i kontrolkami interfejsu użytkownika. Na przykład można użyć paska narzędzi edytora kodowanego testu interfejsu użytkownika do wykonania następujących poleceń:

![Edytor testu interfejsu użytkownika](../test/media/uitesteditor.png)

1. [Znajdź](../ide/finding-and-replacing-text.md) pomaga zlokalizować akcje i kontrolki interfejsu użytkownika.

2. **Delete** usuwa niepożądane akcje interfejsu użytkownika.

3. Zmiana **nazwy** powoduje zmianę nazw dla metod testowych i kontrolek.

4. **Właściwości** otwiera okno **Właściwości** dla wybranego elementu.

5. **Podzielona na nową metodę** pozwala modularyzacji akcje interfejsu użytkownika.

6. **Przenoszenie kodu** dodaje kod niestandardowy do metod testowych.

7. **Wstaw opóźnienie przed** dodaniem pauzy przed akcją interfejsu użytkownika określoną w milisekundach.

8. **Znajdź formant interfejsu użytkownika** identyfikuje lokalizację kontrolki w interfejsie użytkownika testowanej aplikacji.

9. **Znajdź wszystkie** ułatwia sprawdzenie właściwości kontrolki i znaczących zmian w kontrolkach aplikacji.

Po otwarciu pliku *UIMap. UITest* powiązanego z kodowanym TESTem interfejsu użytkownika, kodowany test interfejsu użytkownika otwiera się w **Edytorze KODOWANEGO testu interfejsu użytkownika**. W poniższych procedurach opisano sposób lokalizowania i edytowania metod testowych oraz właściwości akcji interfejsu użytkownika oraz kontrolek przy użyciu paska narzędzi edytora i menu skrótów.

## <a name="open-a-coded-ui-test"></a>Otwieranie kodowanego testu interfejsu użytkownika

Za pomocą **edytora kodowanego testu interfejsu użytkownika**można wyświetlać i edytować swój kodowany test interfejsu użytkownika oparty na języku Visual C# i Visual Basic.

![Edytowanie menu kontekstowego za pomocą konstruktora kodowanego testu interfejsu użytkownika](../test/media/editcodeduitest.png)

W **Eksplorator rozwiązań**Otwórz menu skrótów dla *UIMap. UITest* i wybierz polecenie **Otwórz**. Kodowany test interfejsu użytkownika jest wyświetlany w **Edytorze kodowanego testu interfejsu użytkownika**. Teraz można wyświetlać i edytować zarejestrowane metody, akcje i odpowiadające im kontrolki w kodowanym teście interfejsu użytkownika.

> [!TIP]
> Po wybraniu akcji interfejsu użytkownika, która znajduje się w metodzie w okienku **akcje interfejsu użytkownika** , odpowiadający jej formant zostanie wyróżniony. Możesz również zmodyfikować akcję interfejsu użytkownika lub właściwości kontrolek.

## <a name="modify-ui-action-and-control-properties"></a>Modyfikuj właściwości akcji i kontrolki interfejsu użytkownika

Za pomocą edytora kodowanego testu interfejsu użytkownika można szybko zlokalizować i wyświetlić wszystkie akcje interfejsu użytkownika w metodach testowych. Po wybraniu akcji interfejsu użytkownika w edytorze, odpowiadający jej formant zostanie automatycznie wyróżniony. Analogicznie, jeśli wybierzesz kontrolkę, skojarzone akcje interfejsu użytkownika zostaną wyróżnione. Po wybraniu akcji interfejsu użytkownika lub kontrolki, można łatwo użyć okna **Właściwości** , aby zmodyfikować właściwości, które odpowiadają.

![Właściwości akcji interfejsu użytkownika](../test/media/codeduiedituiaction.png)

Aby zmodyfikować właściwości akcji interfejsu użytkownika, w okienku **Akcja interfejsu użytkownika** rozwiń metodę testową zawierającą akcję interfejsu użytkownika, dla której chcesz edytować właściwości, wybierz akcję interfejsu użytkownika, a następnie zmodyfikuj właściwości przy użyciu okno właściwości.

Na przykład jeśli serwer jest niedostępny i masz akcję interfejsu użytkownika skojarzoną z przeglądarką sieci Web, która **przechodzi do strony sieci Web http: \/ /Contoso1/default.aspx**, można zmienić adres URL na `http://Contoso2/default.aspx` .

![Właściwości kontrolki](../test/media/codeduitestcontrolprop.png)

Modyfikowanie właściwości kontrolki odbywa się w taki sam sposób, jak akcje interfejsu użytkownika. W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę, którą chcesz edytować, i zmodyfikuj jej właściwości przy użyciu okna **Właściwości** .

Na przykład deweloper mógł zmienić właściwość **(ID)** w kontrolce Button w kodzie źródłowym testowanej aplikacji z "idSubmit" na "idLogin". Po zmianie właściwości **(ID)** w aplikacji kodowany test interfejsu użytkownika nie będzie mógł zlokalizować kontrolki przycisku i zakończy się niepowodzeniem. W takim przypadku tester może otworzyć kolekcję **Właściwości wyszukiwania** i zmienić właściwość **ID** tak, aby odpowiadała nowej wartości używanej przez dewelopera w aplikacji. Tester może również zmienić **przyjazną** wartość właściwości Nazwa z "Prześlij" do "login". Wprowadzając tę zmianę, skojarzona akcja interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika zostaje zaktualizowana z "Wybierz przycisk" Prześlij "do" Wybierz "przycisk" Login' ".

Po zakończeniu modyfikacji Zapisz zmiany w pliku *UIMap. Designer* , wybierając pozycję **Zapisz** na pasku narzędzi programu Visual Studio.

### <a name="tips"></a>Porady

- Jeśli okno **Właściwości** nie jest wyświetlane, naciśnij i przytrzymaj klawisz **Alt** podczas naciskania klawisza **Enter**lub naciśnij klawisz **F4**.

- Aby cofnąć wprowadzone zmiany właściwości, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl** + **z**.

- Aby otworzyć narzędzie **Znajdź i Zamień** w programie Visual Studio, można użyć przycisku **Znajdź** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Następnie można użyć kontrolki **Znajdź** , aby zlokalizować akcję interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. Na przykład możesz spróbować znaleźć przycisk "kliknij" Login' ". Może to być przydatne w przypadku dużych testów. Nie można użyć funkcji Replace w narzędziu **Znajdź i Zamień** w edytorze kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz Znajdowanie formantów w [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md).

- Czasami może być trudne Wizualizacja, gdzie kontrolki znajdują się w interfejsie użytkownika testowanej aplikacji. Jedną z możliwości edytora kodowanego testu interfejsu użytkownika jest możliwość wybrania kontrolki wymienionej na mapie formantów interfejsu użytkownika i wyświetlenia jej lokalizacji w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie kontrolki interfejsu użytkownika w testowanej aplikacji](#locate-a-ui-control-in-the-application-under-test) znajdującej się w dalszej części tego artykułu.

- Może być konieczne rozszerzenie kontrolki kontenera zawierającej kontrolkę, którą chcesz edytować. Aby uzyskać więcej informacji, zobacz [lokalizowanie kontrolki i jej elementów podrzędnych](#locate-a-control-and-its-descendants) znajdujących się w dalszej części tego artykułu.

## <a name="delete-unwanted-ui-actions"></a>Usuń niepożądane akcje interfejsu użytkownika

Można łatwo usunąć niepożądane akcje interfejsu użytkownika w kodowanym teście interfejsu użytkownika.

![Usuń akcję interfejsu użytkownika](../test/media/codeduideleteuiaction.png)

W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która zawiera akcję interfejsu użytkownika, którą chcesz usunąć. Otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz polecenie **Usuń**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Podziel metodę testową na dwie oddzielne metody

Można podzielić metodę testową, aby udoskonalić lub modularyzacji akcje interfejsu użytkownika. Na przykład, test może mieć pojedynczą metodę testową z akcjami interfejsu użytkownika w dwóch kontrolkach kontenera. Akcje interfejsu użytkownika mogą być lepiej modularne w dwóch metodach odpowiadających jednemu kontenerowi.

![Podziel metodę testową](../test/media/codeduitestsplitmethod1.png)

![Dwie metody testowe](../test/media/codeduitestsplitmethod2.png)

W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która ma zostać podzielona na dwie oddzielne metody, a następnie wybierz akcję interfejsu użytkownika, w której chcesz rozpocząć nową metodę testową. Otwórz menu skrótów dla akcji interfejsu użytkownika, a następnie wybierz polecenie **Podziel na nową metodę**lub wybierz przycisk **Podziel na nową metodę** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Nowa metoda testowa zostanie wyświetlona w okienku **akcje interfejsu użytkownika** . Zawiera akcje interfejsu użytkownika, rozpoczynając od akcji, w której został określony podział.

Po zakończeniu dzielenia metody Zapisz zmiany w pliku *UIMap. Designer* , wybierając pozycję **Zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> W przypadku podziału metody należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, która ma zostać utworzona, jeśli nadal chcesz, aby te akcje interfejsu użytkownika zostały uwzględnione. Podczas dzielenia metody zostanie wyświetlone okno dialogowe Microsoft Visual Studio. Ostrzega o tym, że musisz zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, którą chcesz utworzyć. Wybierz opcję **tak**.

### <a name="tips"></a>Porady

- Aby cofnąć podział, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl** + **Z**.

- Nową metodę można zmienić. Wybierz go w okienku **akcje interfejsu użytkownika** i wybierz przycisk **Zmień nazwę** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.

   -lub-

   Otwórz menu skrótów dla nowej metody testowej i wybierz polecenie **Zmień nazwę**.

   Pojawi się okno dialogowe programu Microsoft Visual Studio. Ostrzega o tym, że należy zmodyfikować kod odwołujący się do tej metody. Wybierz opcję **tak**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Przenieś metodę testową do pliku UIMap, aby ułatwić dostosowanie

Jeśli określisz, że jedna z metod testowych w kodowanym teście interfejsu użytkownika wymaga kodu niestandardowego, musisz przenieść ją do pliku *UIMap.cs* lub *UIMap. vb* . W przeciwnym razie kod zostanie nadpisany po każdym ponownym skompilowaniu kodowanego testu interfejsu użytkownika. Jeśli nie przeniesiesz metody, kod niestandardowy zostanie nadpisany za każdym razem, gdy test zostanie ponownie skompilowany.

W okienku **Akcja interfejsu użytkownika** wybierz metodę testową, która ma zostać przeniesiona do pliku *UIMap.cs* lub *UIMap. vb* , aby ułatwić niestandardowe funkcje kodu, które nie zostaną zastąpione podczas ponownej kompilacji kodu testowego. Następnie wybierz przycisk **Przenieś kod** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika lub Otwórz menu skrótów dla metody testowej i wybierz polecenie **Przenieś kod**. Metoda testowa jest usuwana z pliku *UIMap. UITest* i nie jest już wyświetlana w okienku **akcje interfejsu użytkownika** . Aby edytować przeniesiony plik testowy, Otwórz plik *UIMap.cs* lub *UIMap. vb* z **Eksplorator rozwiązań**.

Po zakończeniu przeniesienia metody Zapisz zmiany w pliku *UIMap. Designer* , wybierając pozycję **Zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> Po przeniesieniu metody nie można już jej edytować za pomocą edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Podczas przenoszenia metody wyświetlane jest okno dialogowe Microsoft Visual Studio. Ostrzega o tym, że metoda zostanie przeniesiona z pliku *UIMap. UITest* do pliku *UIMap.cs* lub *UIMap. vb* i nie będzie już można edytować metody przy użyciu edytora kodowanego testu interfejsu użytkownika. Wybierz opcję **tak**.

### <a name="tips"></a>Porady

Aby cofnąć przeniesienie, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl** + **Z**. Należy jednak ręcznie usunąć kod z pliku *UIMap.cs* lub *UIMap. vb* .

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Lokalizowanie kontrolki interfejsu użytkownika w testowanej aplikacji

Czasami może być trudne Wizualizacja, gdzie kontrolki znajdują się w interfejsie użytkownika testowanej aplikacji. Jedną z możliwości edytora kodowanego testu interfejsu użytkownika jest możliwość wybrania kontrolki wymienionej na mapie formantów interfejsu użytkownika i wyświetlenia jej lokalizacji w testowanej aplikacji. Za pomocą funkcji **lokalizowania kontrolki interfejsu użytkownika** w testowanej aplikacji można także sprawdzić modyfikacje właściwości wyszukiwania dokonane w formancie.

![Lokalizowanie kontrolki interfejsu użytkownika](../test/media/codeduilocatecontrol.png)

![Kontrolka znajdująca się w testowanej aplikacji](../test/media/codeduilocatecontrol2.png)

W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę, którą chcesz zlokalizować w aplikacji skojarzonej z testem. Następnie otwórz menu skrótów dla kontrolki, a następnie wybierz pozycję **Zlokalizuj formant interfejsu użytkownika**. W testowanej aplikacji kontrolka jest oznaczona niebieską krawędzią.

> [!NOTE]
> Przed zlokalizowaniem kontrolki interfejsu użytkownika Sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

### <a name="tips"></a>Porady

Możesz użyć opcji **Znajdź wszystko** , aby sprawdzić, czy wszystkie kontrolki w kontenerze mogą być prawidłowo zlokalizowane. Ta opcja jest opisana w następnej sekcji.

## <a name="locate-a-control-and-its-descendants"></a>Lokalizowanie formantu i jego elementów podrzędnych

Można sprawdzić, czy wszystkie kontrolki w kontenerze mogą być prawidłowo zlokalizowane w interfejsie użytkownika testowanej aplikacji. Może to pomóc w sprawdzeniu zmian właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto, jeśli wprowadzono znaczące zmiany w interfejsie użytkownika testowanej aplikacji, można sprawdzić, czy istniejące właściwości wyszukiwania kontrolki są nadal poprawne.

![Lokalizowanie wszystkich formantów podrzędnych](../test/media/codeduilocateall.png)

![Wszystkie kontrolki zlokalizowane](../test/media/codeduilocateall2.png)

W okienku **mapy formantów interfejsu użytkownika** Wybierz kontrolkę kontenera, którą chcesz zlokalizować, i Wyświetl wszystkie obiekty podrzędne. Następnie otwórz menu skrótów dla kontrolki i wybierz pozycję **Znajdź wszystkie**. Formant kontenera i wszystkie jego elementy podrzędne są oznaczone w edytorze kodowanego testu interfejsu użytkownika z zielonym znacznikiem wyboru lub czerwoną literą "X". Znaczniki te informują o tym, czy kontrolki zostały pomyślnie umieszczone w testowanej aplikacji.

> [!NOTE]
> Przed zlokalizowaniem formantów interfejsu użytkownika Sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

## <a name="insert-a-delay-before-a-ui-action"></a>Wstaw opóźnienie przed akcją interfejsu użytkownika

Czasami możesz chcieć, aby test czekał na pewne zdarzenia, takie jak okno, które ma zostać wyświetlone, pasek postępu, który znika i tak dalej. Za pomocą edytora kodowanego testu interfejsu użytkownika można to osiągnąć, wstawiając opóźnienie przed akcją interfejsu użytkownika. Można określić, ile sekund ma mieć opóźnienie.

![Wstaw opóźnienie przed akcją interfejsu użytkownika](../test/media/codeduidelay.png)

![Opóźnienie dodane z 5 sekund](../test/media/codeduidealy2.png)

W okienku **Akcja interfejsu użytkownika** rozwiń metodę testową, która zawiera akcję interfejsu użytkownika, do której chcesz wstawić opóźnienie. Wybierz akcję interfejsu użytkownika. Następnie otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz polecenie **Wstaw opóźnienie przed**. Opóźnienie jest wstawiane i wyróżniane przed wybraną akcją interfejsu użytkownika o następującym tekście: **poczekaj 1 sekund na opóźnienie użytkownika między akcjami**. W oknie **Właściwości** Zmień wartość właściwości **opóźnienie** na żądaną liczbę milisekund.

Po wstawieniu opóźnienia Zapisz zmiany w pliku *UIMap. Designer* , wybierając pozycję **Zapisz** na pasku narzędzi programu Visual Studio.

Aby upewnić się, że określony formant jest dostępny przed akcją interfejsu użytkownika, należy rozważyć dodanie niestandardowego kodu do metody testowej przy użyciu odpowiedniej metody UITestControl. WaitForControlXXX (). Aby uzyskać więcej informacji, zobacz [Tworzenie kodowanych testów interfejsu użytkownika w przypadku określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Zobacz też

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanego testu interfejsu użytkownika opartego na danych](../test/creating-a-data-driven-coded-ui-test.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
