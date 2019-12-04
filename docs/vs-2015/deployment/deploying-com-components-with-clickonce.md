---
title: Wdrażanie składników COM za pomocą technologii ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c83367881b7ed6a69fe10af8b7c68eb1692e3e6
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706894"
---
# <a name="deploying-com-components-with-clickonce"></a>Wdrażanie składników COM za pomocą technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wdrożenie starszych składników COM było tradycyjnie trudnym zadaniem. Składniki muszą być zarejestrowane globalnie i w ten sposób mogą spowodować niepożądane skutki uboczne między nakładającymi się aplikacjami. Ta sytuacja zazwyczaj nie jest problemem w aplikacjach .NET Framework, ponieważ składniki są całkowicie izolowane do aplikacji lub są zgodne ze sobą. Program Visual Studio umożliwia wdrażanie izolowanych składników COM w systemie operacyjnym Windows XP lub nowszym.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapewnia łatwy i bezpieczny mechanizm wdrażania aplikacji .NET. Jeśli jednak aplikacje korzystają ze starszych składników modelu COM, należy wykonać dodatkowe kroki w celu ich wdrożenia. W tym temacie opisano sposób wdrażania izolowanych składników COM i odwołań do natywnych składników (na przykład z Visual Basic 6,0 C++lub wizualizacji).  
  
 Aby uzyskać więcej informacji na temat wdrażania izolowanych składników COM, zobacz [uproszczenie wdrażania aplikacji za pomocą technologii ClickOnce i com bez rejestracji](/archive/msdn-magazine/2005/april/simplify-app-deployment-with-clickonce-and-registration-free-com).  
  
## <a name="registration-free-com"></a>COM bez rejestracji  
 COM bez rejestracji to nowa technologia wdrażania i aktywowania izolowanych składników COM. Działa przez umieszczenie wszystkich informacji o bibliotece typów składników i informacje o rejestracji, które są zazwyczaj instalowane w rejestrze systemu do pliku XML o nazwie Manifest, przechowywane w tym samym folderze, w którym znajduje się aplikacja.  
  
 Izolowanie składnika modelu COM wymaga, aby był on zarejestrowany na komputerze dewelopera, ale nie musi być zarejestrowany na komputerze użytkownika końcowego. Aby izolować składnik modelu COM, wystarczy ustawić właściwość **izolowany** odwołania na **wartość true**. Domyślnie ta właściwość ma wartość **false**, co oznacza, że powinna być traktowana jako zarejestrowane odwołanie com. Jeśli ta właściwość ma **wartość true**, powoduje to wygenerowanie manifestu dla tego składnika w czasie kompilacji. Powoduje również, że odpowiednie pliki zostaną skopiowane do folderu aplikacji podczas instalacji.  
  
 Gdy Generator manifestu napotyka odizolowane odwołanie COM, wylicza wszystkie `CoClass` wpisów w bibliotece typów składnika, dopasowuje każdy wpis z odpowiednimi danymi rejestracyjnymi i generuje definicje manifestu dla wszystkich klas COM w pliku biblioteki typów.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Wdrażanie składników COM bez rejestracji za pomocą technologii ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologia wdrażania jest odpowiednia do wdrażania izolowanych składników COM, ponieważ zarówno [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], jak i bezpłatna rejestracja COM wymagają, aby składnik miał manifest do wdrożenia.  
  
 Zazwyczaj autor składnika powinien dostarczyć manifest. Jeśli nie, program Visual Studio może jednak automatycznie wygenerować manifest dla składnika modelu COM. Generowanie manifestu jest wykonywane podczas procesu publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md). Ta funkcja pozwala również wykorzystać starsze składniki, które zostały utworzone we wcześniejszych środowiskach programistycznych, takich jak Visual Basic 6,0.  
  
 Istnieją dwa sposoby [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia składników COM:  
  
- Użyj programu inicjującego, aby wdrożyć składniki COM. działa to na wszystkich obsługiwanych platformach.  
  
- Użyj natywnej izolacji składnika (nazywanej również niezależną rejestracją COM). Ta wartość będzie jednak działać tylko w systemie operacyjnym Windows XP lub nowszym.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Przykład izolowania i wdrażania prostego składnika COM  
 Aby zademonstrować wdrożenie składnika COM bez rejestracji, w tym przykładzie zostanie utworzona aplikacja oparta na systemie Windows w Visual Basic odwołująca się do izolowanego macierzystego składnika COM utworzonego przy użyciu Visual Basic 6,0 i wdrażania go przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 Najpierw należy utworzyć natywny składnik COM:  
  
##### <a name="to-create-a-native-com-component"></a>Aby utworzyć natywny składnik COM  
  
1. Korzystając z Visual Basic 6,0, w menu **plik** kliknij polecenie **Nowy**, a następnie pozycję **projekt**.  
  
2. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual Basic** i wybierz projekt **ActiveX DLL** . W polu **Nazwa** wpisz `VB6Hello`.  
  
    > [!NOTE]
    > W przypadku modelu COM bez rejestracji są obsługiwane tylko typy projektów ActiveX DLL i ActiveX Control. Nie są obsługiwane typy projektów ActiveX EXE i dokumentów ActiveX.  
  
3. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Class1. vb** , aby otworzyć Edytor tekstu.  
  
4. W Class1. vb Dodaj następujący kod po wygenerowaniu kodu dla metody `New`:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. Kompiluj składnik. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.  
  
> [!NOTE]
> Model COM bez rejestracji obsługuje tylko typy projektów DLL i COM Controls. Nie można używać exe z modelem COM bez rejestracji.  
  
 Teraz można utworzyć aplikację opartą na systemie Windows i dodać do niej odwołanie do składnika COM.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Aby utworzyć aplikację opartą na systemie Windows przy użyciu składnika COM  
  
1. Korzystając z Visual Basic, w menu **plik** kliknij polecenie **Nowy**, a następnie **projekt**.  
  
2. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual Basic** i wybierz pozycję **aplikacja systemu Windows**. W polu **Nazwa** wpisz `RegFreeComDemo`.  
  
3. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** , aby wyświetlić odwołania do projektu.  
  
4. Kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.  
  
5. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **Przeglądaj** , przejdź do VB6Hello. dll, a następnie wybierz ją.  
  
    Odwołanie **VB6Hello** pojawia się na liście odwołań.  
  
6. Wskaż **Przybornik**, wybierz kontrolkę **przycisk** i przeciągnij ją do formularza **Form1** .  
  
7. W oknie **Właściwości** ustaw właściwość **Text** przycisku na **Hello**.  
  
8. Kliknij dwukrotnie przycisk, aby dodać kod procedury obsługi, a w pliku kodu Dodaj kod, tak aby program obsługi odczytuje w następujący sposób:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Uruchom aplikację. W menu **debugowanie** kliknij **Rozpocznij debugowanie**.  
  
   Następnie musisz odizolować formant. Każdy składnik COM używany przez aplikację jest reprezentowany w projekcie jako odwołanie COM. Te odwołania są widoczne w węźle **odwołania** w oknie **Eksplorator rozwiązań** . (Należy zauważyć, że można dodać odwołania bezpośrednio przy użyciu polecenia **Dodaj odwołanie** w menu **projekt** lub pośrednio przeciągając kontrolkę ActiveX do formularza).  
  
   Poniższe kroki pokazują, jak izolować składnik modelu COM i opublikować zaktualizowaną aplikację zawierającą wyizolowaną kontrolkę:  
  
##### <a name="to-isolate-a-com-component"></a>Aby wyizolować składnik COM  
  
1. W **Eksplorator rozwiązań**w węźle **odwołania** wybierz odwołanie **VB6Hello** .  
  
2. W oknie **Właściwości** Zmień wartość właściwości **izolowanej** z **false** na **true**.  
  
3. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.  
  
   Teraz, po naciśnięciu klawisza F5, aplikacja działa zgodnie z oczekiwaniami, ale jest teraz uruchomiona w obszarze COM bez rejestracji. Aby to potwierdzić, spróbuj wyrejestrować składnik VB6Hello. dll i uruchomić RegFreeComDemo1. exe poza środowiskiem IDE programu Visual Studio. Tym razem, gdy przycisk zostanie kliknięty, nadal działa. Jeśli tymczasowo zmienisz nazwę manifestu aplikacji, wystąpi błąd.  
  
> [!NOTE]
> Istnieje możliwość symulowania nieobecności składnika COM przez tymczasowe Wyrejestrowanie. Otwórz wiersz polecenia, przejdź do folderu systemowego, wpisując `cd /d %windir%\system32`, a następnie Wyrejestruj składnik, wpisując `regsvr32 /u VB6Hello.dll`. Możesz zarejestrować go ponownie, wpisując `regsvr32 VB6Hello.dll`.  
  
 Ostatnim krokiem jest opublikowanie aplikacji przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Aby opublikować aktualizację aplikacji za pomocą izolowanego składnika COM  
  
1. W menu **kompilacja** kliknij pozycję **Publikuj RegFreeComDemo**.  
  
    Zostanie wyświetlony Kreator publikacji.  
  
2. W Kreatorze publikowania Określ lokalizację na dysku komputera lokalnego, na którym możesz uzyskać dostęp do opublikowanych plików i je przeanalizować.  
  
3. Kliknij przycisk **Zakończ** , aby opublikować aplikację.  
  
   W przypadku badania opublikowanych plików należy zauważyć, że plik Sysmon. ocx jest dołączony. Formant jest całkowicie odizolowany od tej aplikacji, co oznacza, że jeśli komputer użytkownika końcowego ma inną aplikację przy użyciu innej wersji formantu, nie może zakłócać działania tej aplikacji.  
  
## <a name="referencing-native-assemblies"></a>Odwołujące się do zestawów natywnych  
 Program Visual Studio obsługuje odwołania do natywnych Visual Basic C++ 6,0 lub zestawów; takie odwołania są nazywane odwołaniami macierzystymi. Można sprawdzić, czy odwołanie jest natywne, sprawdzając, czy właściwość **typu pliku** jest ustawiona na **natywny** lub **ActiveX**.  
  
 Aby dodać odwołanie natywne, użyj polecenia **Dodaj odwołanie** , a następnie przejdź do manifestu. Niektóre składniki umieszczają manifest wewnątrz biblioteki DLL. W takim przypadku można po prostu wybrać bibliotekę DLL, a program Visual Studio doda ją jako odwołanie natywne, jeśli wykryje, że składnik zawiera osadzony manifest. Program Visual Studio będzie również automatycznie obejmował wszystkie zależne pliki lub zestawy wymienione w manifeście, jeśli znajdują się w tym samym folderze co składnik, do którego się odwołuje.  
  
 Izolacja formantów COM ułatwia wdrażanie składników COM, które nie mają jeszcze manifestów. Jeśli jednak składnik jest dostarczany z manifestem, można odwoływać się bezpośrednio do manifestu. W rzeczywistości należy zawsze używać manifestu dostarczonego przez autora składnika, wszędzie tam, gdzie jest to możliwe, zamiast używać **izolowanej** właściwości.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Ograniczenia dotyczące wdrożenia składnika COM bez rejestracji  
 Model COM bez rejestracji zapewnia wyraźne korzyści w porównaniu z tradycyjnymi technikami wdrażania. Istnieje jednak kilka ograniczeń i ostrzeżenia, które również należy wymusić. Największe ograniczenie polega na tym, że działa tylko w systemie Windows XP lub nowszym. Implementacja COM bez rejestracji wymaga zmian w sposób, w jaki składniki są ładowane w podstawowym systemie operacyjnym. Niestety, nie ma warstwy wsparcia niskiego poziomu dla modelu COM bez rejestracji.  
  
 Nie każdy składnik jest odpowiednim kandydatem dla modelu COM bez rejestracji. Składnik nie jest odpowiedni, jeśli którykolwiek z następujących warunków jest spełniony:  
  
- Składnik jest serwerem poza procesem. Serwery EXE nie są obsługiwane; Obsługiwane są tylko biblioteki DLL.  
  
- Składnik jest częścią systemu operacyjnego lub jest składnikiem systemowym, takim jak XML, Internet Explorer lub Microsoft Data Access Components (MDAC). Należy postępować zgodnie z zasadami redystrybucji autora składnika; Skontaktuj się z dostawcą.  
  
- Składnik jest częścią aplikacji, takiej jak Microsoft Office. Na przykład nie należy próbować izolować modelu obiektów programu Microsoft Excel. Jest to część pakietu Office i może być używana tylko na komputerze z zainstalowanym pełnym produktem pakietu Office.  
  
- Składnik jest przeznaczony do użycia jako dodatek lub przystawka, na przykład dodatek pakietu Office lub kontrolka w przeglądarce sieci Web. Takie składniki wymagają zwykle pewnego rodzaju schematu rejestracji zdefiniowanego przez środowisko hostingu wykraczające poza zakres samego manifestu.  
  
- Składnik zarządza urządzeniem fizycznym lub wirtualnym dla systemu, na przykład sterownika urządzenia dla buforu wydruku.  
  
- Składnik to pakiet redystrybucyjny dostępu do danych. Aplikacje danych zazwyczaj wymagają osobnego pakietu redystrybucyjnego dostępu do danych, aby można go było uruchomić. Nie należy podejmować próby izolowania składników, takich jak Microsoft ADO Data Control, Microsoft OLE DB lub Microsoft Data Access Components (MDAC). Zamiast tego, jeśli aplikacja używa programu MDAC lub SQL Server Express, należy ustawić je jako wymagania wstępne; Zobacz [jak: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  W niektórych przypadkach może być możliwe, aby deweloper składnika mógł go przeprojektować pod kątem COM bez rejestracji. Jeśli nie jest to możliwe, można nadal tworzyć i publikować aplikacje, które są od nich zależne za pośrednictwem standardowego planu rejestracji przy użyciu programu inicjującego. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
  Składnik COM może być odizolowany tylko raz dla każdej aplikacji. Na przykład nie można izolować tego samego składnika COM z dwóch różnych projektów **biblioteki klas** , które są częścią tej samej aplikacji. Wykonanie tej czynności spowoduje ostrzeżenie kompilacji, a aplikacja nie będzie mogła zostać załadowana w czasie wykonywania. Aby uniknąć tego problemu, firma Microsoft zaleca Hermetyzowanie składników modelu COM w jednej bibliotece klas.  
  
  Istnieje kilka scenariuszy, w których rejestracja COM jest wymagana na komputerze dewelopera, nawet jeśli wdrożenie aplikacji nie wymaga rejestracji. Właściwość `Isolated` wymaga zarejestrowania składnika COM na komputerze dewelopera, aby automatycznie wygenerować manifest podczas kompilacji. Nie ma możliwości przechwytywania rejestracji, które wywołują rejestrację automatyczną podczas kompilacji. Ponadto wszelkie klasy, które nie są jawnie zdefiniowane w bibliotece typów, nie zostaną odzwierciedlone w manifeście. W przypadku korzystania ze składnika COM z istniejącym manifestem, takim jak odwołanie natywne, składnik może nie być zarejestrowany w czasie projektowania. Jednak rejestracja jest wymagana, jeśli składnik jest formantem ActiveX i chcesz go umieścić w **przyborniku** i projektancie Windows Forms.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
