---
title: Edytowanie kodowanych testów interfejsu użytkownika, za pomocą edytora testu kodowanego interfejsu użytkownika | Dokumentacja firmy Microsoft
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2cb53bfc500edbf46f277dd86e2c035461d9f9af
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416501"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edycja zakodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor kodowanego testu interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika, możesz zlokalizować, wyświetlić i edytować właściwości swoje metody testowe i działania interfejsu użytkownika. Ponadto można użyć mapy formantów interfejsu użytkownika, możesz wyświetlać i edytować ich odpowiednie metody kontroli.  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Dlaczego należy to zrobić?  
 Za pomocą edytora testu interfejsu użytkownika jest szybsza i bardziej efektywne niż edytowanie kodu w metodach testów kodowanego interfejsu użytkownika za pomocą edytora kodu. Za pomocą interfejsu użytkownika edytora kodowanego testu, można użyć narzędzi i menu skrótów szybko zlokalizować i modyfikować wartości właściwości skojarzone z działania interfejsu użytkownika i kontrolek. Na przykład służy interfejs użytkownika edytora kodowanego testu na pasku narzędzi do wykonywania następujących poleceń:  
  
 ![Edito testu interfejsu użytkownika](../test/media/uitesteditor.png "UITestEditor")  
  
1. [Znajdź](../ide/finding-and-replacing-text.md) ułatwia wykrywanie, akcje interfejsu użytkownika i kontrolek.  
  
2. [Usuń](#CodedUITestEditor_DeleteUIActions) spowoduje usunięcie niepożądanych akcji UI.  
  
3. **Zmień nazwę** zmiany nazwy dla metody testowe i formanty.  
  
4. **Właściwości** zostanie otwarte okno właściwości dla wybranego elementu.  
  
5. [Podziel do nowej metody](#CodedUITestEditor_SplitMethods) umożliwia modularyzacji działania interfejsu użytkownika.  
  
6. [Przenieś kod](#CodedUITestEditor_MoveMethods) dodaje niestandardowy kod do metod badania.  
  
7. [Wstaw opóźnienie przed](#CodedUITestEditor_InsertDelay) dodaje Wstrzymaj przed akcją UI wyrażona w milisekundach.  
  
8. [Zlokalizuj formant interfejsu użytkownika](#CodedUITestEditor_LocateUIControl) identyfikuje położenie formantu w Interfejsie użytkownika aplikacji w ramach testu.  
  
9. [Zlokalizuj wszystkie](#CodedUITestEditor_LocateDecendants) upewnieniu się, kontrolować właściwość i znaczące zmiany i kontrolki w aplikacji.  
  
## <a name="how-do-i-do-this"></a>Jak to zrobić?  
 W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], otwieranie pliku UIMap.uitest powiązane z kodowanego testu interfejsu użytkownika, w projekcie kodowanego testu interfejsu użytkownika będą automatycznie wyświetlać kodowanego testu interfejsu użytkownika w edytora testu interfejsu użytkownika. W poniższych procedurach opisano, jak można zlokalizować i edytować swoje metody testowe i właściwości działania interfejsu użytkownika i kontrolek przy użyciu edytora narzędzi i menu skrótów.  
  
## <a name="open-a-coded-ui-test"></a>Otwórz kodowanego testu interfejsu użytkownika  
 Można wyświetlać i edytować swoje Visual C# i Visual Basic na podstawie kodowanego testu interfejsu użytkownika za pomocą edytora testu interfejsu użytkownika.  
  
 ![Menu kontekstowe edycji z kodowanego testu interfejsu użytkownika](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 W Eksploratorze rozwiązań Otwórz menu skrótów dla **UIMap.uitest** i wybierz polecenie **Otwórz**. Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Można teraz wyświetlać i edytować, zarejestrowane metody, działania i odpowiednie metody kontroli w kodowanym teście interfejsu użytkownika.  
  
> [!TIP]
> Po wybraniu akcji interfejsu użytkownika, który znajduje się w metodzie, w **akcji UI** zostanie wyróżniona w okienku odpowiedni formant. Można również zmodyfikować właściwości formantów lub działania interfejsu użytkownika.  
  
 *Nie widzę* edytora kodowanego testu interfejsu użytkownika.  
 Być może używasz wersji programu Visual Studio Enterprise wcześniejszych niż 2012. Edytor kodowanego testu interfejsu użytkownika było również dostępne w Visual Studio 2010 Feature Pack 2 z subskrypcją MSDN. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
## <a name="CodedUITestEditor_EditActionAndControlProperties"></a> Modyfikowanie właściwości akcji UI oraz odpowiadające im właściwości kontrolki  
 Za pomocą edytora testu interfejsu użytkownika, możesz szybko znaleźć i wyświetlić wszystkie akcje interfejsu użytkownika w swoich metod testowych. Po wybraniu akcji interfejsu użytkownika w edytorze odpowiedni formant automatycznie zostanie wyróżniona. Podobnie jeśli wybranie kontrolki skojarzonych z nimi działań interfejsu użytkownika są wyróżnione. Po wybraniu akcji interfejsu użytkownika lub kontrolki, następnie jest łatwe do zmodyfikowania właściwości, które odnoszą się do jego oknie dialogowym właściwości.  
  
 ![Właściwości akcji UI](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Edycja właściwości akcji UI  
  
 Aby zmodyfikować właściwości dla akcji interfejsu użytkownika w **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz edytować właściwości, wybierz działania interfejsu użytkownika, a następnie zmodyfikuj właściwości w oknie właściwości.  
  
 Na przykład jeśli serwer nie jest dostępny i ma akcji interfejsu użytkownika skojarzonego z przeglądarką sieci Web, stanów **przejdź do strony sieci Web "<http://Contoso1/default.aspx’>**, można zmienić adres URL do `‘ http://Contoso2/default.aspx’`.  
  
 ![Właściwości formantu](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Edycja właściwości kontrolki  
  
 Modyfikowanie właściwości kontrolki odbywa się w taki sam sposób jak działania interfejsu użytkownika. W **mapy formantów UI** okienku zaznacz formant, który chcesz edytować i modyfikowania jego właściwości w oknie właściwości.  
  
 Na przykład, być może zmieniono Deweloper **(ID)** właściwości kontrolki przycisku w kodzie źródłowym aplikacji testowane z "idSubmit" do "idLogin." Za pomocą **(ID)** właściwości zmienione w aplikacji, nie będzie można znaleźć formantu przycisku kodowany test interfejsu użytkownika i zakończy się niepowodzeniem. W takim przypadku można otworzyć tester **wyszukującą** kolekcji i zmień **identyfikator** właściwość, aby pasowała do nowej wartości, używany przez dewelopera aplikacji. Tester może również ulec zmianie **przyjazną nazwę** wartości właściwości z "Prześlij" do "Logowanie". Przez wprowadzenie tej zmiany, skojarzonej akcji interfejsu użytkownika w interfejsie użytkownika edytora kodowanego testu został zaktualizowany z "Wybierz"Prześlij"button" do "Wybierz"Login"button."  
  
 Po zakończeniu modyfikacji, Zapisz zmiany w pliku UIMap.Designer, wybierając **Zapisz** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paska narzędzi.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") , jeśli nie zostanie wyświetlone okno właściwości, naciśnij i przytrzymaj **Alt** podczas, gdy użytkownik naciśnie klawisz **Enter**, lub też nacisnąć klawisz **F4**.  
  
- ![Porada](../test/media/tip.png "Porada") Aby cofnąć wprowadzone zmiany właściwości, zaznacz **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z.  
  
- ![Porada](../test/media/tip.png "Porada") można użyć **znaleźć** przycisk na pasku narzędzi edytora kodowanego testu interfejsu użytkownika, aby otworzyć narzędzie Znajdź i Zamień w programie Visual Studio. Znajdź formant można następnie użyć do zlokalizowania działania interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. Na przykład, możesz spróbować znaleźć "kliknij przycisk"Logowanie"." Może to być przydatne w testach dużych. Należy pamiętać, że nie można użyć funkcji replace, za pomocą narzędzia Znajdź i Zamień w interfejsie użytkownika edytora kodowanego testu. Aby uzyskać więcej informacji, zobacz Znajdź w kontrolce [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).  
  
- ![Porada](../test/media/tip.png "Porada") czasami może być trudne do wizualizacji, gdzie kontrolki znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać kontrolkę mapy formantów interfejsu użytkownika na liście i wyświetlić jego lokalizację w testowanej aplikacji. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Lokalizowanie kontrolki interfejsu użytkownika w aplikacji poddawanej testowi](#CodedUITestEditor_LocateUIControl) znajduje się dalej poniżej w tym temacie.  
  
- ![Porada](../test/media/tip.png "Porada") może być konieczne rozwinąć kontrolki kontenera, który zawiera formant, który chcesz edytować. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Lokalizowanie formantu i jego elementy potomne](#CodedUITestEditor_LocateDecendants) znajduje się dalej poniżej w tym temacie.  
  
## <a name="CodedUITestEditor_DeleteUIActions"></a> Usuwanie niepożądanych akcji UI  
 Można łatwo usunąć niepożądanych akcji UI w kodowanego testu interfejsu użytkownika.  
  
 ![Usuń działania interfejsu użytkownika](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 W **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz usunąć. Otwórz menu skrótów dla akcji interfejsu użytkownika, a następnie wybierz **Usuń**.  
  
## <a name="CodedUITestEditor_SplitMethods"></a> Podziel metody testowej na dwa odrębne metody  
 Możesz podzielić metodę testową, aby zawęzić lub modularyzację działania interfejsu użytkownika. Na przykład test może być metodą jeden test za pomocą akcji interfejsu użytkownika w dwóch kontrolek w kontenerze. Akcje interfejsu użytkownika musi być lepiej modularized za pomocą dwóch metod, które odnoszą się do jednego kontenera.  
  
 ![Metoda testowa Splt](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Dwie metody testów](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 W **działania interfejsu użytkownika** okienku rozwiń metodę testową, która ma zostać podzielona na dwie odrębne metody i wybieranie akcji interfejsu użytkownika, którego nowej metody testowej, aby rozpocząć. Albo otwórz menu skrótów dla działania interfejsu użytkownika, a następnie wybierz **Podziel do nowej metody**, lub wybierz **Podziel do nowej metody** przycisk na pasku narzędzi edytora kodowanego testu interfejsu użytkownika. Nowa metoda testu jest wyświetlana w okienku Akcje interfejsu użytkownika. Zawiera ona działania interfejsu użytkownika, zaczynając od akcji, gdzie określone podziału.  
  
 Po wykonaniu dzielenia metody, należy zapisać zmiany w pliku UIMap.Designer, wybierając **Zapisz** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paska narzędzi.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Istotne problemy**  
  
- ![Ikona ostrzegawcza](../test/media/caution.gif "Przestroga") **ostrzeżenia:** Jeśli podzieli metody należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby wywoływał również nową metodę, którą zamierzasz utworzyć, jeśli nadal chcesz te akcje interfejsu użytkownika uwzględnione. Podczas podziału metody zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że należy zmodyfikować każdy kod, który wywołuje istniejącą metodę, aby wywoływał również nową metodę, którą chcesz utworzyć. Wybierz **tak**.  
  
  **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") Aby cofnąć podziału, wybierz opcję **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z.  
  
- ![Porada](../test/media/tip.png "Porada") można zmienić nazwę nowej metody. Wybierz je w okienku Akcje interfejsu użytkownika, a następnie wybierz **Zmień nazwę** przycisku na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.  
  
   —lub—  
  
   Otwórz menu skrótów dla nowego metoda testowa i wybierz polecenie **Zmień nazwę**.  
  
   Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że należy zmodyfikować każdy kod odwołujący się do metody. Wybierz **tak**.  
  
## <a name="CodedUITestEditor_MoveMethods"></a> Przenieś metody testowej do pliku UIMap w celu ułatwienia dostosowywania  
 Jeśli stwierdzisz, że jeden swoje metody testowe w interfejsie użytkownika usług kodowany test wymaga kodu niestandardowego, przenieś go do pliku UIMap.cs lub UIMap.vb. W przeciwnym razie kodu zostaną zastąpione po każdym kodowanego testu interfejsu użytkownika jest ponownie kompilowana. Jeśli metoda nie jest przeniesienie, niestandardowy kod zostaną zastąpione każdorazowo, gdy test jest ponownie kompilowana.  
  
 W **działania interfejsu użytkownika** okienku, wybierz metodę testową, która ma zostać przeniesiony do pliku UIMap.cs lub UIMap.vb w celu ułatwienia działania kodu niestandardowego zostaną zastąpione, gdy kod testu jest ponownie kompilowana. Następnie wybierz pozycję **Przenieś kod** znajdujący się na pasku narzędzi edytora testu interfejsu użytkownika lub Otwórz menu skrótów dla metody testu i wybierz pozycję **Przenieś kod**. Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować plik testu, który został przeniesiony, otwórz UIMap.cs lub UIMap.vb plik z Eksploratora rozwiązań.  
  
 Po zakończeniu przenoszenia metody, należy zapisać zmiany w pliku UIMap.Designer, wybierając **Zapisz** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paska narzędzi.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Istotne problemy**  
  
- ![Ikona ostrzegawcza](../test/media/caution.gif "Przestroga") **ostrzeżenia:** Po przeniesieniu metody mogą nie trzeba już edytować go za pomocą edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Po przeniesieniu metody, zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ma zostać przeniesiona z pliku UIMap.uitest do UIMap.cs lub UIMap.vb, który nie będzie już można edytować metody za pomocą edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.  
  
  **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") Aby cofnąć przeniesienie, zaznacz **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z. Jednakże należy następnie ręcznie usunąć kod w pliku UIMap.cs lub UIMap.vb.  
  
## <a name="CodedUITestEditor_LocateUIControl"></a> Lokalizowanie kontrolki interfejsu użytkownika w testowanej aplikacji  
 Czasami może być trudne do wizualizacji, gdzie kontrolki znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać kontrolkę mapy formantów interfejsu użytkownika na liście i wyświetlić jego lokalizację w testowanej aplikacji. Za pomocą **zlokalizuj formant interfejsu użytkownika** funkcję na testowaną aplikację można również sprawdzić wyszukiwania właściwości modyfikacje wprowadzone do formantu.  
  
 ![Zlokalizuj formant interfejsu użytkownika](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Formant, który znajduje się w testowanej aplikacji](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 W **mapy formantów UI** okienku, wybierz formant, który ma zostać umieszczony w aplikacji skojarzony z testem. Następnie otwórz menu skrótów dla formantu, a następnie wybierz **zlokalizuj formant interfejsu użytkownika**. W aplikacji, która jest testowana formant jest wyznaczony z niebieskim obramowaniem.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Istotne problemy**  
  
- ![Ikona ostrzegawcza](../test/media/caution.gif "Przestroga") **ostrzeżenia:** Przed kontrolki interfejsu użytkownika możesz zlokalizować, należy sprawdzić, czy jest uruchomiona aplikacja skojarzona z testem.  
  
  **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") Alternatywnie, można użyć **Znajdź wszystkie** opcję, aby sprawdzić, czy wszystkich kontrolek w kontenerze można przechowywać poprawnie. Ta opcja jest opisane w następnej sekcji.  
  
## <a name="CodedUITestEditor_LocateDecendants"></a> Lokalizowanie formantu i jego elementy podrzędne  
 Możesz sprawdzić, czy wszystkich kontrolek w kontenerze można poprawnie znajdować w Interfejsie użytkownika aplikacji w ramach testu. Może to być przydatne podczas weryfikowania zmiany właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto jeśli miały miejsce znaczące zmiany w interfejsie użytkownika aplikacji poddawanej testowi, może się sprawdzić, czy istniejące właściwości wyszukiwania kontrolki są nadal prawidłowe.  
  
 ![Znajdź wszystkie formanty podrzędne](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Wszystkie kontrolki znajdujący się](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 W **mapy formantów UI** okienku zaznacz formant kontenera, który chcesz znaleźć i wyświetlić wszystkie elementy podrzędne dla. Następnie otwórz menu skrótów dla formantu i wybierz **Znajdź wszystkie**. Formant kontenera i wszystkie jego formantów podrzędnych, są oznaczone w interfejsie użytkownika edytora kodowanego testu z zielonym znacznikiem wyboru lub czerwony symbol "X". Te znaczniki pozwalają dowiedzieć się, jeśli kontrolki pomyślnie znajdowały się w testowanej aplikacji.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Istotne problemy**  
  
- ![Ikona ostrzegawcza](../test/media/caution.gif "Przestroga") **ostrzeżenia:** Przed lokalizować kontrolek interfejsu użytkownika, należy sprawdzić, czy aplikacja skojarzona z test jest uruchomiony.  
  
## <a name="CodedUITestEditor_InsertDelay"></a> Wstawianie opóźnienia przed akcją UI  
 Czasami możesz chcieć wykonać próbę, poczekaj, aż niektóre zdarzenia, takiego jak okna wyświetlany pasek postępu znikną i tak dalej. Za pomocą edytora kodowanego testu interfejsu użytkownika, można to zrobić, wstawiając opóźnienia przed akcją UI. Można określić, ile sekund ma opóźnienie za.  
  
 ![Wstaw opóźnienie przed akcją UI](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Dodaje się z 5 sekund opóźnienia](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 W **działania interfejsu użytkownika** okienku rozwiń metody testowej, który zawiera działania interfejsu użytkownika, który chcesz wstawić opóźnienie przed. Wybieranie akcji interfejsu użytkownika. Następnie otwórz menu skrótów dla działania interfejsu użytkownika i wybierz polecenie **Wstaw opóźnienie przed**. Opóźnienie jest wstawiany i wyróżnione przed wybranej akcji interfejsu użytkownika w następującym tekstem: **Poczekaj 1 w sekundach dla opóźnienia użytkownika między akcjami**. W oknie Właściwości zmień wartość **opóźnienie** żądaną liczbę milisekund.  
  
 Po zakończeniu Wstawianie opóźnienia, zapisać zmiany w pliku UIMap.Designer, wybierając **Zapisz** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paska narzędzi.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Uwagi**  
  
- ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") Jeśli potrzebujesz upewnić się, że jest określona kontrolka jest dostępny przed akcją UI, należy rozważyć dodanie niestandardowego kodu do metody testowej przy użyciu odpowiednich UITestControl.WaitForControlXXX() Metoda. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Tworzenie kodowanego interfejsu użytkownika testy dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
  **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") Jeśli nie zostanie wyświetlone okno właściwości, naciśnij i przytrzymaj klawisz Alt podczas naciśnij klawisz Enter, lub też nacisnąć klawisz F4.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyczne testowanie interfejsu użytkownika (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Tworzenie na podstawie danych kodowanego testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md)   
 [Generowanie kodowanego testu interfejsu użytkownika na podstawie dotychczasowego rejestrowania akcji](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)   
 [Przewodnik: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
