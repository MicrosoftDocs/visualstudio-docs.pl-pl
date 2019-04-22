---
title: Program Visual Studio Shell (zintegrowany) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87c7b4faaf5aad737c8f7f8b653dbea03bc4de31
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58866778"
---
# <a name="visual-studio-shell-integrated"></a>Program Visual Studio Shell (zintegrowany)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powłoka programu Visual Studio obejmuje zintegrowanego środowiska programistycznego (IDE), debuger oraz integrację kontroli źródła. Nie język programowania jest dołączony. Jednak integrated shell zapewniają strukturę, która pozwala na dodawanie języków programowania.  
  
 Powłoka programu Visual Studio jest faktycznie kombinacji powłoki programu Visual Studio izolowane, a także dodatkowe instalacji, obejmujące określonych składników zintegrowane powłoki.  Shell zintegrowanych aplikacji powinien zawierać zarówno izolowanej powłoki pakietu redystrybucyjnego z [pakiet redystrybucyjny Microsoft Visual Studio Shell (Isolated)](http://go.microsoft.com/fwlink/?LinkId=616022) oraz pakiet redystrybucyjny zintegrowane shell z [programu Microsoft Visual Studio powłoki (Integrated) pakiet redystrybucyjny](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Aby uzyskać dostęp do pakietów redystrybucyjnych powłoki izolowanej i zintegrowanej, pojawi się prośba do wypełnienia ankiety klientów.  Po wypełnieniu ankiety, nastąpi przekierowanie do strony Visual Studio Connect zawierającej łącza pobierania pakietów redystrybucyjnych.  Łącza pobierania podczas kolejnych wizyt w witrynie Visual Studio Connect, w obszarze **programy &#124; VISUAL STUDIO 2015 ZINTEGROWANE i ISOLATED SHELL** kartę.  
  
 Po zainstalowaniu aplikacji zintegrowanych powłoki na tym samym komputerze co pełną wersję programu Visual Studio, składniki aplikacji zostaną zintegrowane bezpośrednio do programu Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funkcje w Integrated Shell  
  
|||  
|-|-|  
|Obszar funkcji|Funkcja|  
|Obsługa języków|-Brak|  
|IDE|<ul><li>Ustawienia<br /><br /> <ul><li>Utwórz ustawienia</li><li>Import i eksport ustawień</li><li>Resetuj ustawienia</li></ul></li><li>**Przybornik** integracji</li><li>**Lista zadań** integracji</li><li>Pomoc w integracji</li><li>**Opcje** okno dialogowe</li><li>Zarządzanie czcionki i kolory</li><li>**Dane wyjściowe** okna</li><li>**Polecenie** okna</li><li>Zarządzanie oknem</li><li>Polecenia, menu i powiązań klawiszy</li><li>Środowisko uruchomieniowe języka specyficznego dla domeny (DSL)</li></ul>|  
|System projektu i typów projektów|— Rozwiązania i foldery rozwiązania<br />— Menedżer konfiguracji rozwiązania<br />— Zarządzanie element<br />— Rozwiązania pojedynczego projektu i wielu projektów<br />— Projektant aplikacji (właściwości projektu uproszczony)<br />-Dodaj odwołanie sieci Web<br />-Dodaj odwołanie do usługi<br />Pojedynczego projektu<br />— Typy projektów witryny sieci Web<br />-Projektów aplikacji sieci web|  
|Kompilacja|-Niestandardowych kroków kompilacji w środowisku IDE<br />-Wstępnej kompilacji dla ochrona własności intelektualnej (IP)<br />-Podpisywanie kodu<br />     MSBuild|  
|Edytor|-Przeglądania narzędzia (ujednolicone wyszukiwanie, definicja źródła, dziedziczenie) kodu<br />-Nawigowanie po kodzie<br />— Technologia IntelliSense<br />-Tagi inteligentne<br />-Refaktoryzacji<br />-Pretty listy<br />— Filtrowanie IntelliSense<br />-   **Kod definicji** okna|  
|Projektant|— Windows Presentation Foundation projektanta<br />— Windows Forms Designer<br />-Sieci web projektanta i edytora HTML|  
|Dane|-   **Eksplorator serwera** (uproszczone: tylko dane). Patrz Uwaga 1.<br />-   **Źródła danych** okna<br />-Pełnego zestawu kontrolek danych<br />-Edytor XML<br />-Powiąż dane z lokalnego źródła danych (. MDF lub. MDB)<br />— Powiązanie danych obiekt<br />-Powiąż dane z usługi sieci Web<br />-Powiąż dane z lokalnej bazy danych serwera<br />— Powiązanie danych do zdalnego serwera bazy danych<br />— Narzędzia języka DDL dla danych zdalnych<br />-   **Eksplorator serwera** rozszerzalności ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] przykłady)|  
|Debuger|— Debugowanie lokalne. Patrz Uwaga 2.<br />-Debugowania zarządzanego<br />— Debugowanie lokalne<br />— Dołącz do procesu lokalnego<br />— Dołącz do procesu zdalnego<br />-Delegat anonimowe<br />— Domeny aplikacji<br />— Debugowanie ASPX<br />— Atrybuty<br />-Break podczas Func eval<br />-Punktów przerwania<br />— Punkt przerwania ograniczenia<br />-Stosu wywołań<br />-   **Polecenie** okna<br />— Debugowanie międzywątkowe<br />— Porady dotyczące danych<br />— Wizualizator danych<br />-Obsługa debugera dla Asystentów zarządzanego debugowania (mda)<br />-Obsługa debugera dla typu usługi przesyłania dalej<br />-DTEEvents obsługę OTB<br />-JMC Stepper<br />-Test AppID debugera (DBGCLR)<br />— Profil debuger<br />-Debugera, narzędzia i opcje<br />— Iterator debugowania<br />-Obliczanie wyrażenia czasu projektowania<br />— Ewaluator wyrażeń C#<br />-Dezasemblacji<br />-Edytuj i Kontynuuj<br />-Expression evaluator windows (Czujka, zmienne lokalne, automatyczne)<br />— Pomocnik wyjątek<br />-Wyjątków<br />— Wykonywanie<br />-Ogólne<br />— Wprowadzenie prawo źródła<br />-HPC/debugowanie klastra<br />— Zintegrowane debugowanie wiele języków<br />— Debugowanie międzyoperacyjne<br />Debugowanie just-in time<br />— Debugowanie lokalne<br />-Debugowania zarządzanego<br />-Ręcznej kontroli (okno procesów)<br />-Pamięć<br />-Obsługa minizrzutu<br />— Moduły<br />-Debugowanie wielu procesów<br />-Debugowanie w trybie macierzystym<br />-New Obsługa aparatu debugowania<br />— Debugowanie zoptymalizowanego kodu<br />-Filtrowania systemu windows output<br />-Przetwarzanie hostingu do debugowania zarządzanego<br />-Procesy<br />-Quickwatch<br />-Rejestrów<br />-Rejestrów na stosie<br />-Zdalnego debugowania<br />— Zwracane wartości<br />-Debugowanie script<br />-Obsługa usługi source<br />— Zabezpieczenia<br />Side-by-side<br />-SQL<br />— Serwer symbol<br />-Punkty śledzenia<br />-Wątku<br />-Wizualizacji<br />-Extensible arkusza stylów języka przekształcenia (XSLT) debugera|  
|Obsługa 64-bitowa|— 64-bitowych debugowania dla kodu zarządzanego i natywnego, wszystkie języki<br />— obsługuje x64 natywne|  
|Kontrola kodu źródłowego (SCC)|-Podstawowa integracja SCC. Patrz Uwaga 3.<br />-Narzędzia i opcje weryfikacji|  
|Rozszerzalność|-Korzystających ze składników pakietów VSPackage i MEF|  
  
## <a name="notes"></a>Uwagi  
  
#### <a name="1-data-tools"></a>1. Narzędzia danych  
 Integrated shell obejmuje bazy danych narzędziami programistycznymi, takimi jak obsługa rozszerzalności danych i uproszczone **Eksploratora rozwiązań**. Jednakże programu SQL Server Express, SQL Reporting i Crystal Reports nie są objęte integrated shell.  
  
#### <a name="2-debugging-support"></a>2. Obsługa debugowania  
 Integrated shell obejmuje tego samego aparatu debugowania, który znajduje się w wersji Community programu Visual Studio. Aparatu debugowania zawiera typowe debuger dla kodu zarządzanego, a także powiązanych funkcji, takich jak uruchamianie, Dołącz, ustaw punkt przerwania, Edytuj i Kontynuuj oraz inne. Jednak aparat debugowania nie obsługuje debugowania bazy danych programu SQL Server.  
  
 Mimo że pomocy technicznej dla debugowanie natywne jest uwzględniony w pakiecie debugera podstawowych, nie można rozszerzyć jej do obsługiwania dodatkowych języków.  
  
#### <a name="3-source-code-control-integration"></a>3. Integracji kontroli kodu źródłowego  
 Integrated shell udostępnia interfejsy API do wykonywania kontroli kodu źródłowego (SCC) i zapewniające składników integracji na podstawie MSSCCI do wspólnej kontroli źródła.  
  
 Integracja SCC nie jest regularne funkcji wersji Pro Visual Studio, integracja SCC znajduje się w integrated shell.  
  
#### <a name="4-build-support"></a>4. Obsługa narzędzia Build  
 Integrated shell oferuje obsługę kompilacji. Można znaleźć informacje o kompilacji w [odwołanie do MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funkcje, które nie są objęte Integrated Shell  
 Poniżej przedstawiono listę funkcji, które nie są uwzględnione w integrated shell:  
  
-   Projektant klas  
  
-   Ochrona preEmptive — Dotfuscator  
  
-   Funkcje językowe  
  
-   VSHost  
  
-   Żadne języki Visual Studio lub ich szablony skojarzonego projektu lub szablony elementów projektu, są uwzględnione w integrated shell. Nie implementacji specyficznych dla języka innych funkcji, dla dołączono przykładowych fragmentów kodu języka Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie programu Visual Studio — omówienie](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)