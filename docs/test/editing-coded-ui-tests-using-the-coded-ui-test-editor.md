---
title: Edytowanie kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88002f4187883d55f22ec9f3dc80f3ceb65e7e48
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784514"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika

Edytor kodowanego testu interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika, możesz zlokalizować, wyświetlić i edytować właściwości swoje metody testowe i działania interfejsu użytkownika. Ponadto można użyć mapy formantów interfejsu użytkownika, możesz wyświetlać i edytować ich odpowiednie metody kontroli.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise
- Kodowane składnik testu interfejsu użytkownika

## <a name="features-of-the-coded-ui-test-editor"></a>Funkcje z edytora testu kodowanego interfejsu użytkownika

Za pomocą edytora testu interfejsu użytkownika jest szybsza i bardziej efektywne niż edytowanie kodu w metodach testów kodowanego interfejsu użytkownika za pomocą edytora kodu. Za pomocą interfejsu użytkownika edytora kodowanego testu, można użyć narzędzi i menu skrótów szybko zlokalizować i modyfikować wartości właściwości skojarzone z działania interfejsu użytkownika i kontrolek. Na przykład służy interfejs użytkownika edytora kodowanego testu na pasku narzędzi do wykonywania następujących poleceń:

![Edytor testu interfejsu użytkownika](../test/media/uitesteditor.png)

1. [Znajdź](../ide/finding-and-replacing-text.md) ułatwia wykrywanie, akcje interfejsu użytkownika i kontrolek.

2. **Usuń** spowoduje usunięcie niepożądanych akcji UI.

3. **Zmień nazwę** zmiany nazwy dla metody testowe i formanty.

4. **Właściwości** otwiera **właściwości** okna dla wybranego elementu.

5. **Podziel do nowej metody** umożliwia modularyzacji działania interfejsu użytkownika.

6. **Przenieś kod** dodaje niestandardowy kod do metod badania.

7. **Wstaw opóźnienie przed** dodaje Wstrzymaj przed akcją UI wyrażona w milisekundach.

8. **Zlokalizuj formant interfejsu użytkownika** identyfikuje położenie formantu w Interfejsie użytkownika aplikacji w ramach testu.

9. **Zlokalizuj wszystkie** upewnieniu się, kontrolować właściwość i znaczące zmiany i kontrolki w aplikacji.

Po otwarciu *UIMap.uitest* pliku przynależność użytkownika kodowany test interfejsu użytkownika kodowany test interfejsu użytkownika, zostanie otwarty w programie **edytora testu interfejsu użytkownika**. W poniższych procedurach opisano, jak można zlokalizować i edytować swoje metody testowe i właściwości działania interfejsu użytkownika i kontrolek przy użyciu edytora narzędzi i menu skrótów.

## <a name="open-a-coded-ui-test"></a>Otwórz kodowanego testu interfejsu użytkownika

Można wyświetlać i edytować swoje Visual C# i Visual Basic na podstawie kodowanego testu interfejsu użytkownika przy użyciu **edytora testu interfejsu użytkownika**.

![Menu kontekstowe edycji z kodowanego testu interfejsu użytkownika](../test/media/editcodeduitest.png)

W **Eksploratora rozwiązań**, otwórz menu skrótów dla *UIMap.uitest* i wybierz polecenie **Otwórz**. Kodowany test interfejsu użytkownika jest wyświetlany w **edytora testu interfejsu użytkownika**. Można teraz wyświetlać i edytować, zarejestrowane metody, działania i odpowiednie metody kontroli w kodowanym teście interfejsu użytkownika.

> [!TIP]
> Po wybraniu akcji interfejsu użytkownika, który znajduje się w metodzie, w **akcji UI** zostanie wyróżniona w okienku odpowiedni formant. Można również zmodyfikować właściwości formantów lub działania interfejsu użytkownika.

## <a name="modify-ui-action-and-control-properties"></a>Zmodyfikuj właściwości akcji i kontrolki interfejsu użytkownika

Za pomocą edytora testu interfejsu użytkownika, możesz szybko znaleźć i wyświetlić wszystkie akcje interfejsu użytkownika w swoich metod testowych. Po wybraniu akcji interfejsu użytkownika w edytorze odpowiedni formant automatycznie zostanie wyróżniona. Podobnie jeśli wybranie kontrolki skojarzonych z nimi działań interfejsu użytkownika są wyróżnione. Po wybraniu akcji interfejsu użytkownika lub kontrolki, następnie jest łatwa w użyciu **właściwości** okna, aby zmodyfikować właściwości, które odnoszą się z nim.

![Właściwości akcji UI](../test/media/codeduiedituiaction.png)

Aby zmodyfikować właściwości dla akcji interfejsu użytkownika w **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz edytować właściwości, wybierz działania interfejsu użytkownika, a następnie zmodyfikuj właściwości w oknie właściwości.

Na przykład jeśli serwer nie jest dostępny i ma akcji interfejsu użytkownika skojarzonego z przeglądarką sieci web, stanów **przejdź do strony sieci Web "<http://Contoso1/default.aspx>"**, można zmienić adres URL do `'http://Contoso2/default.aspx'`.

![Właściwości formantów](../test/media/codeduitestcontrolprop.png)

Modyfikowanie właściwości kontrolki odbywa się w taki sam sposób jak działania interfejsu użytkownika. W **mapy formantów UI** okienku zaznacz formant, który chcesz edytować i modyfikowania jego właściwości, za pomocą **właściwości** okna.

Na przykład, być może zmieniono Deweloper **(ID)** właściwości kontrolki przycisku w kodzie źródłowym aplikacji testowane z "idSubmit" do "idLogin." Za pomocą **(ID)** właściwości zmienione w aplikacji, nie będzie można znaleźć formantu przycisku kodowany test interfejsu użytkownika i zakończy się niepowodzeniem. W takim przypadku można otworzyć tester **wyszukującą** kolekcji i zmień **identyfikator** właściwość, aby pasowała do nowej wartości, używany przez dewelopera aplikacji. Tester może również ulec zmianie **przyjazną nazwę** wartości właściwości z "Prześlij" do "Logowanie". Przez wprowadzenie tej zmiany, skojarzonej akcji interfejsu użytkownika w interfejsie użytkownika edytora kodowanego testu został zaktualizowany z "Wybierz"Prześlij"button" do "Wybierz"Login"button."

Po zakończeniu modyfikacji, czy zapisać zmiany *UIMap.Designer* pliku, wybierając **Zapisz** na pasku narzędzi programu Visual Studio.

### <a name="tips"></a>Porady

- Jeśli **właściwości** nie zostanie wyświetlone okno, naciśnij i przytrzymaj klawisz **Alt** podczas, gdy użytkownik naciśnie klawisz **Enter**, lub naciśnij **F4**.

- Aby cofnąć wprowadzone zmiany właściwości, zaznacz **Cofnij** z **Edytuj** menu lub naciśnij klawisz **Ctrl**+**Z**.

- Możesz użyć **znaleźć** przycisk na pasku narzędzi edytora kodowanego testu interfejsu użytkownika, aby otworzyć **Znajdź i Zamień** narzędzia w programie Visual Studio. Następnie można użyć **znaleźć** formantu, aby zlokalizować działania interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. Na przykład, możesz spróbować znaleźć "kliknij przycisk"Logowanie"." Może to być przydatne w testach dużych. Nie można używać funkcji Zastąp **Znajdź i Zamień** narzędzia w interfejsie użytkownika edytora kodowanego testu. Aby uzyskać więcej informacji, zobacz Znajdź w kontrolce [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

- Czasami może być trudne do wizualizacji, gdzie kontrolki znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać kontrolkę mapy formantów interfejsu użytkownika na liście i wyświetlić jego lokalizację w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [zlokalizuj kontrolkę interfejsu użytkownika w aplikacji poddawanej testowi](#locate-a-ui-control-in-the-application-under-test) znajduje się dalej poniżej w tym artykule.

- Może być konieczne rozwinąć kontrolki kontenera, który zawiera formant, który chcesz edytować. Aby uzyskać więcej informacji, zobacz [zlokalizować formantu i jego elementy potomne](#locate-a-control-and-its-descendants) znajduje się dalej poniżej w tym artykule.

## <a name="delete-unwanted-ui-actions"></a>Usuwanie niepożądanych akcji UI

Można łatwo usunąć niepożądanych akcji UI w kodowanego testu interfejsu użytkownika.

![Usuń działania interfejsu użytkownika](../test/media/codeduideleteuiaction.png)

W **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz usunąć. Otwórz menu skrótów dla akcji interfejsu użytkownika, a następnie wybierz **Usuń**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Podziel metody testowej na dwa odrębne metody

Możesz podzielić metodę testową, aby zawęzić lub modularyzację działania interfejsu użytkownika. Na przykład test może być metodą jeden test za pomocą akcji interfejsu użytkownika w dwóch kontrolek w kontenerze. Akcje interfejsu użytkownika musi być lepiej modularized za pomocą dwóch metod, które odnoszą się do jednego kontenera.

![Podziel metody testowej](../test/media/codeduitestsplitmethod1.png)

![Dwie metody badania](../test/media/codeduitestsplitmethod2.png)

W **działania interfejsu użytkownika** okienku rozwiń metodę testową, która ma zostać podzielona na dwie odrębne metody i wybieranie akcji interfejsu użytkownika, którego nowej metody testowej, aby rozpocząć. Albo otwórz menu skrótów dla działania interfejsu użytkownika, a następnie wybierz **Podziel do nowej metody**, lub wybierz **Podziel do nowej metody** przycisk na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Nowej metody testowej, który pojawia się w **akcji UI** okienka. Zawiera ona działania interfejsu użytkownika, zaczynając od akcji, gdzie określone podziału.

Po wykonaniu dzielenia metody, czy zapisać zmiany *UIMap.Designer* pliku, wybierając **Zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> Jeśli podzieli metody należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby wywoływał również nową metodę, którą zamierzasz utworzyć, jeśli nadal chcesz te akcje interfejsu użytkownika uwzględnione. Podczas podziału metody zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby wywoływał również nową metodę, którą chcesz utworzyć. Wybierz **tak**.

### <a name="tips"></a>Porady

- Aby cofnąć podziału, wybierz opcję **Cofnij** z **Edytuj** menu lub naciśnij klawisz **Ctrl**+**Z**.

- Można zmienić nazwę nowej metody. Zaznacz go w **akcji UI** okienka i wybierz polecenie **Zmień nazwę** przycisku na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.

   —lub—

   Otwórz menu skrótów dla nowego metoda testowa i wybierz polecenie **Zmień nazwę**.

   Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że należy zmodyfikować każdy kod odwołujący się do metody. Wybierz **tak**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Przenieś metody testowej do pliku UIMap w celu ułatwienia dostosowywania

Jeśli stwierdzisz, że jeden swoje metody testowe w interfejsie użytkownika usług kodowany test wymaga kodu niestandardowego, przenieś go do którejkolwiek *UIMap.cs* lub *UIMap.vb* pliku. W przeciwnym razie kodu zostaną zastąpione po każdym kodowanego testu interfejsu użytkownika jest ponownie kompilowana. Jeśli metoda nie jest przeniesienie, niestandardowy kod zostaną zastąpione każdorazowo, gdy test jest ponownie kompilowana.

W **działania interfejsu użytkownika** okienku wybierz metodę badania, jaką chcesz przenieść do *UIMap.cs* lub *UIMap.vb* pliku celu ułatwienia działania kodu niestandardowego, nie będzie zastąpione gdy kod testu jest ponownie kompilowana. Następnie wybierz pozycję **Przenieś kod** znajdujący się na pasku narzędzi edytora testu interfejsu użytkownika lub Otwórz menu skrótów dla metody testu i wybierz pozycję **Przenieś kod**. Metoda testowa jest usuwany z *UIMap.uitest* pliku i nie jest już wyświetlana w **działania interfejsu użytkownika** okienka. Aby edytować plik testu, który został przeniesiony, otwórz *UIMap.cs* lub *UIMap.vb* plik wchodzącej w skład **Eksploratora rozwiązań**.

Po zakończeniu przenoszenia metody, czy zapisać zmiany *UIMap.Designer* pliku, wybierając **Zapisz** na pasku narzędzi programu Visual Studio.

> [!WARNING]
> Po przeniesieniu metody mogą nie trzeba już edytować go za pomocą edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Po przeniesieniu metody, zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ma zostać przeniesiona z *UIMap.uitest* plik *UIMap.cs* lub *UIMap.vb* plik i że nie będzie już można edytować za pomocą metody Edytor testu kodowanego interfejsu użytkownika. Wybierz **tak**.

### <a name="tips"></a>Porady

Aby cofnąć przeniesienie, zaznacz **Cofnij** z **Edytuj** menu lub naciśnij klawisz **Ctrl**+**Z**. Jednakże, należy następnie ręcznie usunąć kod z *UIMap.cs* lub *UIMap.vb* pliku.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Zlokalizuj kontrolkę interfejsu użytkownika w testowanej aplikacji

Czasami może być trudne do wizualizacji, gdzie kontrolki znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać kontrolkę mapy formantów interfejsu użytkownika na liście i wyświetlić jego lokalizację w testowanej aplikacji. Za pomocą **zlokalizuj formant interfejsu użytkownika** funkcję na testowaną aplikację można również sprawdzić wyszukiwania właściwości modyfikacje wprowadzone do formantu.

![Zlokalizuj formant interfejsu użytkownika](../test/media/codeduilocatecontrol.png)

![Formant zlokalizowany w testowanej aplikacji](../test/media/codeduilocatecontrol2.png)

W **mapy formantów UI** okienku, wybierz formant, który ma zostać umieszczony w aplikacji skojarzony z testem. Następnie otwórz menu skrótów dla formantu, a następnie wybierz **zlokalizuj formant interfejsu użytkownika**. W aplikacji, która jest testowana formant jest wyznaczony z niebieskim obramowaniem.

> [!NOTE]
> Przed kontrolki interfejsu użytkownika możesz zlokalizować, należy sprawdzić, czy jest uruchomiona aplikacja skojarzona z testem.

### <a name="tips"></a>Porady

Możesz użyć **Znajdź wszystkie** opcję, aby sprawdzić, czy wszystkich kontrolek w kontenerze można przechowywać poprawnie. Ta opcja jest opisane w następnej sekcji.

## <a name="locate-a-control-and-its-descendants"></a>Zlokalizuj formant i jego elementy podrzędne

Możesz sprawdzić, czy wszystkich kontrolek w kontenerze można poprawnie znajdować w Interfejsie użytkownika aplikacji w ramach testu. Może to być przydatne podczas weryfikowania zmiany właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto jeśli miały miejsce znaczące zmiany w interfejsie użytkownika aplikacji poddawanej testowi, może się sprawdzić, czy istniejące właściwości wyszukiwania kontrolki są nadal prawidłowe.

![Znajdź wszystkie formanty podrzędne](../test/media/codeduilocateall.png)

![Wszystkie kontrolki znajdujący się](../test/media/codeduilocateall2.png)

W **mapy formantów UI** okienku zaznacz formant kontenera, który chcesz znaleźć i wyświetlić wszystkie elementy podrzędne dla. Następnie otwórz menu skrótów dla formantu i wybierz **Znajdź wszystkie**. Formant kontenera i wszystkie jego formantów podrzędnych, są oznaczone w interfejsie użytkownika edytora kodowanego testu z zielonym znacznikiem wyboru lub czerwony symbol "X". Te znaczniki pozwalają dowiedzieć się, jeśli kontrolki pomyślnie znajdowały się w testowanej aplikacji.

> [!NOTE]
> Przed lokalizować kontrolek interfejsu użytkownika, należy sprawdzić, czy aplikacja skojarzona z test jest uruchomiony.

## <a name="insert-a-delay-before-a-ui-action"></a>Wstawianie opóźnienia przed akcją UI

Czasami możesz chcieć wykonać próbę, poczekaj, aż niektóre zdarzenia, takiego jak okna wyświetlany pasek postępu znikną i tak dalej. Za pomocą edytora kodowanego testu interfejsu użytkownika, można to zrobić, wstawiając opóźnienia przed akcją UI. Można określić, ile sekund ma opóźnienie za.

![Wstaw opóźnienie przed akcją UI](../test/media/codeduidelay.png)

![Dodaje się z 5 sekund opóźnienia](../test/media/codeduidealy2.png)

W **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz wstawić opóźnienie przed. Wybieranie akcji interfejsu użytkownika. Następnie otwórz menu skrótów dla działania interfejsu użytkownika i wybierz polecenie **Wstaw opóźnienie przed**. Opóźnienie jest wstawiany i wyróżnione przed wybranej akcji interfejsu użytkownika w następującym tekstem: **Poczekaj 1 w sekundach dla opóźnienia użytkownika między akcjami**. W **właściwości** okna, zmień wartość **opóźnienie** żądaną liczbę milisekund.

Po zakończeniu Wstawianie opóźnienia, czy zapisać zmiany *UIMap.Designer* pliku, wybierając **Zapisz** na pasku narzędzi programu Visual Studio.

Jeśli potrzebujesz upewnić się, że jest określona kontrolka jest dostępny przed akcją UI, należy rozważyć dodanie niestandardowego kodu do metody testowej przy użyciu metody odpowiedniej UITestControl.WaitForControlXXX(). Aby uzyskać więcej informacji, zobacz [podejmowanie kodowanych testów interfejsu użytkownika dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie opartych na danych kodowanego testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)