---
title: Wdrażanie składników COM za pomocą technologii ClickOnce | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9422d1c2a185e223b35bc16ad892282ca1c2a420
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786162"
---
# <a name="deploying-com-components-with-clickonce"></a>Wdrażanie składników COM za pomocą technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wdrażanie składników COM, starszy tradycyjnie było trudne zadanie. Składniki potrzebne do zarejestrowania globalnie i ten sposób może spowodować niepożądane skutki uboczne między nakładającymi się aplikacje. Ta sytuacja zwykle nie jest to problem występujący w aplikacjach .NET Framework, ponieważ składniki są całkowicie odizolowane do aplikacji lub są zgodne z side-by-side. Program Visual Studio umożliwia wdrażanie izolowane składniki COM na wyższe system operacyjny lub Windows XP.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] udostępnia mechanizm łatwy i bezpieczny do wdrażania aplikacji .NET. Jednak jeśli aplikacje korzystają z starszych składników modelu COM, należy wykonać dodatkowe kroki dotyczące wdrażania ich. W tym temacie opisano sposób wdrażania izolowane składniki COM i odwołanie składnikami macierzystymi (na przykład z języka Visual C++ lub Visual Basic 6.0).  
  
 Aby uzyskać więcej informacji na temat wdrażania izolowane składniki COM, zobacz "Uprość wdrażanie aplikacji za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i rejestracji wolnego modelu COM" w [ http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM bez rejestrowania  
 COM bez rejestrowania się nowej technologii związanych z wdrażaniem i aktywowanie izolowane składniki COM. Działa przez umieszczenie biblioteki typów wszystkich składników i informacje o rejestracji, który jest zwykle instalowany w rejestrze systemu do pliku XML o nazwie manifestu, przechowywane w tym samym folderze co aplikacja.  
  
 Izolowanie składnika modelu COM wymaga on być zarejestrowany na komputerze dewelopera, ale nie musi być zarejestrowana na komputerze użytkownika końcowego. Aby wyizolować składnika modelu COM, ustawiono wszystko, czego potrzebujesz, aby wykonać swoje odwołanie **izolowany** właściwości **True**. Domyślnie wartość tej właściwości jest równa **False**, wskazujący, że powinny być traktowane jako odwołanie COM zarejestrowane. Jeśli ta właściwość jest **True**, spowoduje wygenerowanie manifestu do wygenerowania tego składnika w czasie kompilacji. Powoduje również odpowiadające im pliki będą kopiowane do folderu aplikacji podczas instalacji.  
  
 Gdy generator manifestu napotka odwołanie COM izolowany, wylicza wszystkie `CoClass` wpisów w bibliotece typów składnika, dopasowanie każdego wpisu z jego odpowiadające im dane rejestracji i generowanie manifestu definicji dla modelu COM klasy w pliku biblioteki typów.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Wdrażanie składników COM bez rejestrowania za pomocą technologii ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologii wdrażania jest dobrze nadaje się do wdrożenia składników COM izolowany, ponieważ oba [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i rejestracji wolnego modelu COM wymagają, że składnik mieć manifestu w celu wdrożenia.  
  
 Zazwyczaj autora składnika powinny dostarczyć manifestu. Jeśli nie, jednak program Visual Studio jest zdolny do generowania manifestu automatycznie składnika modelu COM. Generowanie manifestu jest wykonywane podczas [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] publikowania procesu; Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md). Ta funkcja umożliwia również wykorzystywać starszej wersji składników, które utworzone w starszych środowiskach programistycznych, takich jak Visual Basic 6.0.  
  
 Istnieją dwa sposoby, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdraża składniki COM:  
  
-   Wdrażanie składników COM; przy użyciu programu inicjującego to działa na wszystkich obsługiwanych platformach.  
  
-   Przy użyciu składnika macierzystego izolacji (znany także jako rejestracji wolnego modelu COM) wdrażania. Jednak ta opcja zadziała tylko w Windows XP lub nowszej systemu operacyjnego.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Przykład izolowanie i wdrażania prostego składnika modelu COM  
 W celu przedstawienia wdrożenie składnika COM bez rejestrowania, w tym przykładzie zostanie tworzenie aplikacji z systemem Windows w języku Visual Basic, który odwołuje się do izolowanego składnika COM natywne utworzone przy użyciu języka Visual Basic 6.0 i wdróż je za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 Najpierw należy utworzyć natywnych składnika modelu COM:  
  
##### <a name="to-create-a-native-com-component"></a>Do tworzenia natywnych składnika modelu COM  
  
1.  Za pomocą języka Visual Basic 6.0 z **pliku** menu, kliknij przycisk **New**, następnie **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **języka Visual Basic** a następnie wybierz węzeł **ActiveX DLL** projektu. W **nazwa** wpisz `VB6Hello`.  
  
    > [!NOTE]
    >  Obsługiwane są tylko typy projektu ActiveX biblioteki DLL i kontrolki ActiveX z COM bez rejestrowania; Typy projektu ActiveX EXE i dokumentu ActiveX nie są obsługiwane.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Class1.vb** można otworzyć edytora tekstu.  
  
4.  W Class1.vb, Dodaj następujący kod po kod generowany dla `New` metody:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Utwórz składnik. Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
> [!NOTE]
>  COM bez rejestrowania obsługuje tylko bibliotek DLL i COM kontroluje typów projektów. Nie można używać pliku exe z rejestracji wolnego modelu COM.  
  
 Teraz możesz utworzyć aplikację z systemem Windows i dodać odwołanie do składnika modelu COM do niego.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Aby tworzyć aplikacje oparte na Windows za pomocą składnika modelu COM  
  
1. W języku Visual Basic z **pliku** menu, kliknij przycisk **New**, następnie **projektu**.  
  
2. W **nowy projekt** okno dialogowe, wybierz opcję **języka Visual Basic** a następnie wybierz węzeł **aplikacji Windows**. W **nazwa** wpisz `RegFreeComDemo`.  
  
3. W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisk, aby wyświetlić odwołania do projektu.  
  
4. Kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie** z menu kontekstowego.  
  
5. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **Przeglądaj** kartę, przejdź do VB6Hello.dll, a następnie wybierz ją.  
  
    A **VB6Hello** odwołania, który pojawia się na liście odwołania.  
  
6. Wskaż **przybornika**, wybierz opcję **przycisk** sterowania, a następnie przeciągnij go **Form1** formularza.  
  
7. W **właściwości** okna, ustaw właściwość **tekstu** właściwości **Hello**.  
  
8. Kliknij dwukrotnie przycisk aby dodać kod procedury obsługi, a w pliku kodu, Dodaj kod, tak aby program obsługi o następującej treści:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Uruchom aplikację. Z **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
   Następnie trzeba izolować formantu. Każdy składnik COM, używanych przez aplikację jest reprezentowana w projekcie jako odwołanie COM. Te odwołania są widoczne w obszarze **odwołania** w węźle **Eksploratora rozwiązań** okna. (Zwróć uwagę, że można dodawać odwołuje się bezpośrednio przy użyciu **Dodaj odwołanie** polecenie **projektu** menu lub pośrednio, przeciągając kontrolki ActiveX na formularzu.)  
  
   Poniższe kroki pokazują jak izolowania składników COM i opublikować zaktualizowaną aplikację zawierająca formant izolowanym:  
  
##### <a name="to-isolate-a-com-component"></a>Do izolowania składników COM  
  
1. W **Eksploratora rozwiązań**w **odwołania** węzeł **VB6Hello** odwołania.  
  
2. W **właściwości** okna, zmień wartość właściwości **izolowany** właściwość **False** do **True**.  
  
3. Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
   Teraz, po naciśnięciu klawisza F5, działa aplikacja, zgodnie z oczekiwaniami, ale teraz działa on w ramach rejestracji wolnego modelu COM. W celu potwierdzenia, spróbuj wyrejestrowywanie składników VB6Hello.dll i uruchomić RegFreeComDemo1.exe poza programem Visual Studio IDE. Tym razem po kliknięciu przycisku nadal działa. Jeśli zmienisz tymczasowo manifest aplikacji, ponownie powiedzie.  
  
> [!NOTE]
>  Brak składnika modelu COM można symulować tymczasowo wyrejestrowując go. Otwórz wiersz polecenia, przejdź do folderu systemu, wpisując `cd /d %windir%\system32`, następnie należy wyrejestrować składnika, wpisując `regsvr32 /u VB6Hello.dll`. Można zarejestrować go ponownie, wpisując `regsvr32 VB6Hello.dll`.  
  
 Ostatnim krokiem jest do publikowania aplikacji przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Aby opublikować aktualizacje aplikacji przy użyciu izolowanego składnika modelu COM  
  
1. Z **kompilacji** menu, kliknij przycisk **publikowania RegFreeComDemo**.  
  
    Pojawi się Kreator publikacji.  
  
2. W Kreatorze publikowania należy określać lokalizacji na dysku komputera lokalnego, w którym dostęp i przejrzyj pliki opublikowane.  
  
3. Kliknij przycisk **Zakończ** Aby opublikować aplikację.  
  
   Podczas badania opublikowane pliki, można zauważyć, czy plik sysmon.ocx jest dołączony. Kontrolka jest całkowicie odizolowane do tej aplikacji, co oznacza, że komputerze użytkownika końcowego jest inna aplikacja używa innej wersji kontrolki, nie może kolidować do za pomocą tej aplikacji.  
  
## <a name="referencing-native-assemblies"></a>Odwoływanie się do zestawów natywnych  
 Program Visual Studio obsługuje odwołania do natywnego języka Visual Basic 6.0 lub zestawów języka C++; odwołania te są nazywane odwołania natywne. Można sprawdzić, czy odwołanie jest natywny, upewniając się, że jego **typ pliku** właściwość jest ustawiona na **natywnych** lub **ActiveX**.  
  
 Aby dodać odwołanie natywne, użyj **Dodaj odwołanie** polecenia, a następnie przejdź do manifestu. Niektóre składniki umieść manifest wewnątrz pliku DLL. W takich przypadkach można po prostu wybierz bibliotekę DLL, sama i programu Visual Studio doda go jako odwołanie natywne jeśli wykryje, że składnik zawiera manifest wbudowany. Program Visual Studio zawierają również automatycznie ani plików zależnych zestawów, wymienione w manifeście, jeśli są one w tym samym folderze co składnik odwołania.  
  
 COM formant izolację sprawia, że można łatwo wdrażać składniki COM, które nie zostały jeszcze manifestów. Jednak jeśli składnik jest dostarczany z manifestu, można się odwołać manifest bezpośrednio. W rzeczywistości należy zawsze używać manifestu, dostarczone przez autora składnika, tam gdzie to możliwe, zamiast używania **izolowany** właściwości.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Ograniczenia dotyczące wdrożenia bez rejestracji składników COM  
 COM bez rejestrowania zalety wyczyść za pośrednictwem techniki wdrażania tradycyjnych. Istnieją pewne ograniczenia i ostrzeżenia, które należy również wskazać. Największe ograniczenie polega na tym, że działa tylko w Windows XP lub nowszym. Implementacja COM bez rejestrowania wymagało wprowadzenia zmian do sposobu ładowania składników w podstawowego systemu operacyjnego. Niestety nie ma żadnych warstwę obsługi niskiego poziomu dla rejestracji wolnego modelu COM.  
  
 Nie każdy składnik jest odpowiednia kandydatem do rejestracji wolnego modelu COM. Składnik nie jest odpowiedni w przypadku spełnienia dowolnego z następujących czynności:  
  
- Składnik to serwer spoza procesu. Plik EXE serwery są nieobsługiwane. obsługiwane są tylko bibliotek DLL.  
  
- Składnik jest częścią systemu operacyjnego lub jest składnikiem systemu, takich jak XML, Internet Explorer lub Microsoft Data Access Components (MDAC). Należy przestrzegać zasad redystrybucji autora składnika; Skontaktuj się z dostawcą.  
  
- Składnik jest częścią aplikacji, takich jak Microsoft Office. Na przykład nie należy podejmować izolowania modelu obiektów programu Microsoft Excel. To jest częścią pakietu Office i można używać tylko na komputerze przy użyciu pełnej pakietu Office.  
  
- Składnik jest przeznaczony do użytku jako dodatek lub przystawki, na przykład dodatku pakietu Office lub kontrolki w przeglądarce sieci Web. Takie składniki zwykle wymagają od pewnego rodzaju rejestracji schemat zdefiniowany przez środowisko hostingu, która wykracza poza zakres manifestu, sam.  
  
- Składnik zarządza urządzeniem fizycznym lub wirtualnym systemu, na przykład sterownik urządzenia Bufor wydruku.  
  
- Składnik jest Data Access redistributable. Aplikacje obsługujące dane wymagają oddzielnych dostępu do danych do dystrybucji przed uruchomieniem przez nich. Nie należy próbować izolowania składników, takich jak formant danych ADO firmy Microsoft, Microsoft OLE DB lub Microsoft Data Access Components (MDAC). Zamiast tego Jeśli aplikacja używa programu MDAC lub SQL Server Express, należy ustawić je jako warunki wstępne; zobacz [jak: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  W niektórych przypadkach może być możliwe dla dewelopera składnika przeprojektować go dla rejestracji wolnego modelu COM. Jeśli nie jest to możliwe, można nadal tworzyć i publikować aplikacje, które zależą od nich za pośrednictwem schemat standardowy rejestracji, za pomocą programu inicjującego. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
  Składnik COM może być tylko raz izolowane, każdej aplikacji. Na przykład nie można odizolować tego samego składnika modelu COM z dwóch różnych **biblioteki klas** projektów, które są częścią tej samej aplikacji. To spowoduje ostrzeżenia kompilacji, a aplikacja nie będzie można załadować w czasie wykonywania. Aby uniknąć tego problemu, firma Microsoft zaleca hermetyzację składników COM w bibliotece pojedynczą klasę.  
  
  Istnieje kilka scenariuszy, w których COM na komputerze dewelopera, wymagana jest rejestracja, mimo, że wdrożenie aplikacji nie wymaga rejestracji. `Isolated` Właściwość wymaga można zarejestrować składnika COM na komputerze dewelopera w celu automatycznego generowania manifestu podczas kompilacji. Nie ma żadnych możliwości przechwytywania rejestracji, które wywołują rejestracji automatycznej podczas kompilacji. Ponadto wszystkie klasy, które nie zostały jawnie zdefiniowany w bibliotece typów nie zostaną odzwierciedlone w manifeście. Podczas używania składnika modelu COM z istniejącego manifestu, takich jak odwołanie natywne, składnik nie może być konieczne można zarejestrować w czasie projektowania. Jednak rejestracja jest wymagana, jeśli składnik to formant ActiveX i mają zostać uwzględnione w **przybornika** i projektanta Windows Forms.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
