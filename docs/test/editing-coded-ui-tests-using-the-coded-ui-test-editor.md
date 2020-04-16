---
title: Edytowanie kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8df6d1ea44cb9737c39653366c7b35823051d5f6
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445041"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edytowanie zakodowanych testów interfejsu użytkownika przy użyciu edytora kodowanych testów interfejsu użytkownika

Edytor kodowanych testów interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą Edytora testów kodowanych interfejsu użytkownika, można zlokalizować, wyświetlić i edytować właściwości metod testowych i akcji interfejsu użytkownika. Ponadto można użyć mapy sterowania interfejsu użytkownika, aby wyświetlić i edytować odpowiednie formanty.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise
- Składnik testu kodowany interfejs użytkownika

## <a name="features-of-the-coded-ui-test-editor"></a>Funkcje edytora kodowanych testów interfejsu użytkownika

Za pomocą Edytora testów kodowanych interfejsu użytkownika jest szybsze i bardziej wydajne niż edytowanie kodu w kodowanych metod testowania interfejsu użytkownika przy użyciu Edytora kodu. Za pomocą Edytora kodowanych testów interfejsu użytkownika można użyć paska narzędzi i menu skrótów, aby szybko zlokalizować i zmodyfikować wartości właściwości skojarzone z akcjami interfejsu użytkownika i formantami. Na przykład można użyć paska narzędzi Edytora testów kodowanych interfejsu użytkownika do wykonywania następujących poleceń:

![Edytor testów interfejsu użytkownika](../test/media/uitesteditor.png)

1. [Znajdź](../ide/finding-and-replacing-text.md) pomaga zlokalizować akcje interfejsu użytkownika i formanty.

2. **Polecenie Usuń** usuwa niechciane akcje interfejsu użytkownika.

3. **Zmień nazwę** zmienia nazwy metod testowych i formantów.

4. **Właściwości** otwiera okno **Właściwości** dla zaznaczonego elementu.

5. **Podział na nową metodę** umożliwia modularyzację akcji interfejsu użytkownika.

6. **Przenieś kod** dodaje kod niestandardowy do metod testowych.

7. **Wstaw opóźnienie przed** dodaje pauzę przed akcją interfejsu użytkownika, określoną w milisekundach.

8. **Zlokalizuj formant interfejsu użytkownika** identyfikuje lokalizację formantu w interfejsie użytkownika aplikacji w ramach testu.

9. **Locate All** pomaga zweryfikować właściwości kontroli i istotnych zmian w formanty aplikacji.

Po otwarciu pliku *UIMap.uitest powiązanego* z kodowanym testem interfejsu użytkownika kodowany test interfejsu użytkownika zostanie otwarty w **edytorze kodowanych testów interfejsu użytkownika**. W poniższych procedurach opisano, jak następnie można zlokalizować i edytować metody testowe i właściwości akcji interfejsu użytkownika i formantów przy użyciu paska narzędzi edytora i menu skrótów.

## <a name="open-a-coded-ui-test"></a>Otwieranie zakodowany test interfejsu użytkownika

Można wyświetlać i edytować test kodowego interfejsu użytkownika oparty na języku Visual C# i Visual Basic za pomocą **Edytora kodowanych testów interfejsu użytkownika.**

![Menu kontekstowe Edytuj za pomocą konstruktora testów kodowanych interfejsu użytkownika](../test/media/editcodeduitest.png)

W **Eksploratorze rozwiązań**otwórz menu skrótów dla *interfejsu użytkownika UIMap.uitest* i wybierz pozycję **Otwórz**. Zakodowany test interfejsu użytkownika jest wyświetlany w **edytorze kodowanych testów interfejsu użytkownika**. Teraz można wyświetlać i edytować zarejestrowane metody, akcje i odpowiednie formanty w kodowanym teście interfejsu użytkownika.

> [!TIP]
> Po wybraniu akcji interfejsu użytkownika, która znajduje się w metodzie w okienku **Akcje interfejsu** użytkownika, odpowiedni formant jest wyróżniony. Można również zmodyfikować akcję interfejsu użytkownika lub właściwości formantu.

## <a name="modify-ui-action-and-control-properties"></a>Modyfikowanie właściwości akcji i kontroli interfejsu użytkownika

Za pomocą Edytora testów kodowanych interfejsu użytkownika, można szybko zlokalizować i wyświetlić wszystkie akcje interfejsu użytkownika w metody testowe. Po wybraniu akcji interfejsu użytkownika w edytorze odpowiedni formant jest automatycznie podświetlany. Podobnie, jeśli wybierzesz formant, skojarzone akcje interfejsu użytkownika są wyróżnione. Po wybraniu akcji interfejsu użytkownika lub formantu, jest to łatwe w użyciu **właściwości** okna, aby zmodyfikować właściwości, które odpowiadają z nim.

![Właściwości akcji interfejsu użytkownika](../test/media/codeduiedituiaction.png)

Aby zmodyfikować właściwości akcji interfejsu użytkownika, w okienku **Akcja interfejsu użytkownika** rozwiń metodę testową zawierającą akcję interfejsu użytkownika, dla której chcesz edytować właściwości, wybierz akcję interfejsu użytkownika, a następnie zmodyfikuj właściwości za pomocą okna Właściwości.

Na przykład, jeśli serwer jest niedostępny i z przeglądarką sieci Web jest skojarzona akcja interfejsu użytkownika, która stanowi **Przejdź do strony sieci Web http:\//Contoso1/default.aspx**, można zmienić adres URL na `http://Contoso2/default.aspx`.

![Właściwości kontrolki](../test/media/codeduitestcontrolprop.png)

Modyfikowanie właściwości formantu odbywa się w taki sam sposób, jak akcje interfejsu użytkownika. W okienku **Mapa sterowania interfejsu** użytkownika zaznacz formant, który chcesz edytować i zmodyfikować jego właściwości za pomocą okna **Właściwości.**

Na przykład deweloper mógł zmienić właściwość **(ID)** na formancie przycisku w kodzie źródłowym testowanego aplikacji z "idSubmit" na "idLogin". Po zmianie właściwości **(ID)** w aplikacji, kodowany test interfejsu użytkownika nie będzie w stanie zlokalizować formantu przycisku i zakończy się niepowodzeniem. W takim przypadku tester można otworzyć **kolekcji Właściwości wyszukiwania** i zmienić właściwość **Id,** aby dopasować nową wartość, która deweloper używany w aplikacji. Tester może również zmienić wartość właściwości **Przyjazna nazwa** z "Prześlij" na "Zaloguj się". Wykonując tę zmianę, skojarzona akcja interfejsu użytkownika w edytorze kodowanych testów interfejsu użytkownika jest aktualizowana z przycisku "Wybierz "Prześlij" na przycisk "Wybierz "Zaloguj".

Po zakończeniu modyfikacji zapisz zmiany w pliku *UIMap.Designer,* wybierając pozycję **Zapisz** na pasku narzędzi programu Visual Studio.

### <a name="tips"></a>Porady

- Jeśli okno **Właściwości** nie jest wyświetlane, naciśnij i przytrzymaj **klawisz Alt** podczas naciskania **klawisza Enter**lub naciśnięcia **klawisza F4**.

- Aby cofnąć wprowadzone zmiany właściwości, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl**+**Z**.

- Przycisk **Znajdź** można użyć na pasku narzędzi edytora kodowany test interfejsu użytkownika, aby otworzyć narzędzie **Znajdź i zamień** w programie Visual Studio. Następnie można użyć **Znajdź** kontrolki, aby zlokalizować akcję interfejsu użytkownika w edytorze kodowany test interfejsu użytkownika. Możesz na przykład spróbować znaleźć przycisk "Kliknij przycisk "Zaloguj się". Może to być przydatne w dużych testach. Nie można użyć funkcji zastępowania w narzędziu **Znajdź i zamień** w Edytorze kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz Znajdowanie formantu w [ciekaniu i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

- Czasami może być trudne do wizualizacji, gdzie formanty znajdują się w interfejsie użytkownika aplikacji w ramach testu. Jedną z możliwości zakodowanego edytora testów interfejsu użytkownika jest to, że można wybrać formant wymieniony na mapie sterowania interfejsu użytkownika i wyświetlić jego lokalizację w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [Lokalizowanie formantu interfejsu użytkownika w testowej aplikacji znajdującej](#locate-a-ui-control-in-the-application-under-test) się poniżej w tym artykule.

- Może być konieczne rozwinięcie formantu kontenera, który zawiera formant, który chcesz edytować. Aby uzyskać więcej informacji, zobacz [Lokalizowanie formantu i jego elementów podrzędnych](#locate-a-control-and-its-descendants) znajdujących się poniżej w tym artykule.

## <a name="delete-unwanted-ui-actions"></a>Usuwanie niechcianych akcji interfejsu użytkownika

Można łatwo usunąć niechciane akcje interfejsu użytkownika w kodowany test interfejsu użytkownika.

![Akcja Usuń interfejs użytkownika](../test/media/codeduideleteuiaction.png)

W okienku **Akcja interfejsu** użytkownika rozwiń metodę testową zawierającą akcję interfejsu użytkownika, którą chcesz usunąć. Otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz pozycję **Usuń**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Podziel metodę testową na dwie oddzielne metody

Można podzielić metodę testu, aby uściślić lub modularyzować akcje interfejsu użytkownika. Na przykład test może mieć jedną metodę testową z akcjami interfejsu użytkownika w dwóch formantów kontenera. Akcje interfejsu użytkownika może być lepiej modularized w dwóch metod, które odpowiadają z jednego kontenera.

![Dzielenie metody testowej](../test/media/codeduitestsplitmethod1.png)

![Dwie metody badań](../test/media/codeduitestsplitmethod2.png)

W okienku **Akcja interfejsu** użytkownika rozwiń metodę testową, którą chcesz podzielić na dwie oddzielne metody i wybierz akcję interfejsu użytkownika, w której ma się rozpocząć nowa metoda testowa. Otwórz menu skrótów dla akcji interfejsu użytkownika, a następnie wybierz pozycję **Podziel na nową metodę**lub wybierz przycisk Podziel na nową **metodę** na pasku narzędzi Coded UI Test Editor. Nowa metoda testowa pojawia się w okienku **Akcje interfejsu** użytkownika. Zawiera akcje interfejsu użytkownika, począwszy od akcji, w której określono podział.

Po zakończeniu dzielenia metody, zapisać zmiany w pliku *UIMap.Designer,* wybierając **zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> Jeśli podzielisz metodę, należy zmodyfikować dowolny kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, którą zamierzasz utworzyć, jeśli nadal chcesz te akcje interfejsu użytkownika uwzględnione. Po podzieleniu metody jest wyświetlane okno dialogowe programu Microsoft Visual Studio. Ostrzega, że należy zmodyfikować dowolny kod, który wywołuje istniejącą metodę, aby również wywołać nową metodę, którą zamierzasz utworzyć. Wybierz **pozycję Tak**.

### <a name="tips"></a>Porady

- Aby cofnąć podział, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl**+**Z**.

- Można zmienić nazwę nowej metody. Zaznacz go w okienku **Akcje interfejsu** użytkownika i wybierz przycisk **Zmień nazwę** na pasku narzędzi Coded UI Test Editor.

   — lub —

   Otwórz menu skrótów dla nowej metody testowej i wybierz pozycję **Zmień nazwę**.

   Pojawi się okno dialogowe programu Microsoft Visual Studio. Ostrzega, że należy zmodyfikować dowolny kod, który odwołuje się do metody. Wybierz **pozycję Tak**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Przenoszenie metody testowej do pliku UIMap w celu ułatwienia dostosowywania

Jeśli okaże się, że jedna z metod testowych w kodowany test interfejsu użytkownika wymaga kodu niestandardowego, należy przenieść go do *pliku UIMap.cs* lub *UIMap.vb.* W przeciwnym razie kod zostanie zastąpiony za każdym razem, gdy kodowany test interfejsu użytkownika zostanie ponownie skompilowany. Jeśli nie przenieść metodę, kod niestandardowy zostanie zastąpiony za każdym razem, gdy test jest ponownie skompilowany.

W okienku **Akcja interfejsu** użytkownika wybierz metodę testową, którą chcesz przenieść do pliku *UIMap.cs* lub *UIMap.vb,* aby ułatwić funkcjonalność kodu niestandardowego, która nie zostanie zastąpiona po ponownym skompilowaniu kodu testowego. Następnie wybierz przycisk **Przenieś kod** na pasku narzędzi Edytor testów kodowanych interfejsu użytkownika lub otwórz menu skrótów dla metody testowej i wybierz polecenie **Przenieś kod**. Metoda testowa jest usuwana z pliku *UIMap.uitest* i nie jest już wyświetlana w okienku **Akcje interfejsu** użytkownika. Aby edytować przeniesiony plik testowy, otwórz *UIMap.cs* lub plik *UIMap.vb* w **Eksploratorze rozwiązań**.

Po zakończeniu przenoszenia metody zapisz zmiany w pliku *UIMap.Designer,* wybierając **pozycję Zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> Po przeniesieniu metody nie można jej już edytować za pomocą edytora kodowanych testów interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Podczas przenoszenia metody jest wyświetlane okno dialogowe programu Microsoft Visual Studio. Ostrzega, że metoda zostanie przeniesiona z pliku *UIMap.uitest* do pliku *UIMap.cs* lub *UIMap.vb* i że nie będzie już można edytować metody za pomocą edytora testów kodowanych interfejsu użytkownika. Wybierz **pozycję Tak**.

### <a name="tips"></a>Porady

Aby cofnąć ruch, wybierz polecenie **Cofnij** z menu **Edycja** lub naciśnij klawisz **Ctrl**+**Z**. Jednak następnie należy ręcznie usunąć kod z *pliku UIMap.cs* lub *UIMap.vb.*

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Lokalizowanie formantu interfejsu użytkownika w badanej aplikacji

Czasami może być trudne do wizualizacji, gdzie formanty znajdują się w interfejsie użytkownika aplikacji w ramach testu. Jedną z możliwości zakodowanego edytora testów interfejsu użytkownika jest to, że można wybrać formant wymieniony na mapie sterowania interfejsu użytkownika i wyświetlić jego lokalizację w testowanej aplikacji. Za pomocą **funkcji Znajdź formant interfejsu użytkownika** w aplikacji w ramach testu można również sprawdzić modyfikacje właściwości wyszukiwania, które zostały wprowadzone do formantu.

![Lokalizowanie kontrolki interfejsu użytkownika](../test/media/codeduilocatecontrol.png)

![Kontrola zlokalizowana w badanych aplikacjach](../test/media/codeduilocatecontrol2.png)

W okienku **Mapy sterowania interfejsu** użytkownika wybierz formant, który chcesz zlokalizować w aplikacji skojarzonej z testem. Następnie otwórz menu skrótów dla formantu, a następnie wybierz pozycję **Znajdź kontrolka interfejsu użytkownika**. W aplikacji, która jest testowana, formant jest oznaczony z niebieskim obramowaniem.

> [!NOTE]
> Przed zlokalizowaniem formantu interfejsu użytkownika sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

### <a name="tips"></a>Porady

Za pomocą opcji **Znajdź wszystko** można sprawdzić, czy wszystkie formanty w kontenerze mogą być poprawnie zlokalizowane. Ta opcja jest opisana w następnej sekcji.

## <a name="locate-a-control-and-its-descendants"></a>Lokalizowanie formantu i jego elementów podrzędnych

Można sprawdzić, czy wszystkie formanty w kontenerze mogą być poprawnie zlokalizowane w interfejsie użytkownika aplikacji w ramach testu. Może to być przydatne w weryfikacji zmian właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto jeśli wystąpiły istotne zmiany w interfejsie użytkownika aplikacji w ramach testu, można sprawdzić, czy istniejące właściwości wyszukiwania formantu są nadal poprawne.

![Znajdź wszystkie kontrolki podrzędne](../test/media/codeduilocateall.png)

![Wszystkie elementy sterujące znajdują się](../test/media/codeduilocateall2.png)

W okienku **Mapy sterowania interfejsu** użytkownika wybierz kontrolkę kontenera, dla której chcesz zlokalizować i wyświetlić wszystkie elementy podrzędne. Następnie otwórz menu skrótów dla formantu i wybierz pozycję **Znajdź wszystko**. Formant kontenera i wszystkie jego formanty podrzędne są oznaczone w edytorze kodowanych testów interfejsu użytkownika za pomocą zielonego znacznika wyboru lub czerwonego znaku "X". Te znaki poinformować, jeśli formanty zostały pomyślnie zlokalizowane w aplikacji w ramach testu.

> [!NOTE]
> Przed zlokalizowaniem formantów interfejsu użytkownika sprawdź, czy aplikacja skojarzona z testem jest uruchomiona.

## <a name="insert-a-delay-before-a-ui-action"></a>Wstawianie opóźnienia przed akcją interfejsu użytkownika

Czasami można wykonać test czekać na pewne zdarzenia wystąpią, takie jak okno, aby pojawić się, pasek postępu zniknąć i tak dalej. Za pomocą Edytora kodowanych testów interfejsu użytkownika, można to zrobić, wstawiając opóźnienie przed akcją interfejsu użytkownika. Można określić, ile sekund ma być opóźnieniem.

![Wstawianie opóźnienia przed akcją interfejsu użytkownika](../test/media/codeduidelay.png)

![Dodano opóźnienie z 5 sekundami](../test/media/codeduidealy2.png)

W okienku **Akcja interfejsu** użytkownika rozwiń metodę testową zawierającą akcję interfejsu użytkownika, która ma zostać wcześniej wstawiona z opóźnieniem. Wybierz akcję interfejsu użytkownika. Następnie otwórz menu skrótów dla akcji interfejsu użytkownika i wybierz polecenie **Wstaw opóźnienie przed**. Opóźnienie jest wstawiane i wyróżniane przed wybraną akcją interfejsu użytkownika z następującym tekstem: **Poczekaj 1 sekundy na opóźnienie użytkownika między akcjami**. W oknie **Właściwości** zmień wartość właściwości **Delay** na żądaną liczbę milisekund.

Po zakończeniu wstawiania opóźnienia zapisz zmiany w pliku *UIMap.Designer,* wybierając **pozycję Zapisz** na pasku narzędzi programu Visual Studio.

Jeśli trzeba upewnić się, że określony formant jest dostępny przed akcją interfejsu użytkownika, należy rozważyć dodanie kodu niestandardowego do metody testowej przy użyciu odpowiedniej metody UITestControl.WaitForControlXXX(). Aby uzyskać więcej informacji, zobacz [Wykonywanie kodowanych testów interfejsu użytkownika czeka na określone zdarzenia podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowego testu interfejsu użytkownika opartego na danych](../test/creating-a-data-driven-coded-ui-test.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowany test interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
