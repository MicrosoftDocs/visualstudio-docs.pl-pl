---
title: Visual Studio Shell (zintegrowany) | Microsoft Docs
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
ms.openlocfilehash: 907b71d82a3c630bedc48209e735d9cf817432ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543159"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (zintegrowany)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zintegrowana powłoka programu Visual Studio obejmuje zintegrowane środowisko programistyczne (IDE), debuger i integrację kontroli źródła. Nie dołączono żadnego języka programowania. Zintegrowana powłoka zapewnia jednak strukturę, która pozwala na dodawanie języków programowania.  
  
 Zintegrowana powłoka programu Visual Studio jest w rzeczywistości kombinacją izolowanej powłoki programu Visual Studio oraz dodatkowej instalacji, która obejmuje zintegrowane składniki powłoki.  Zintegrowana aplikacja powłoki powinna zawierać zarówno pakiet redystrybucyjny izolowanej powłoki, jak i pakiet redystrybucyjny zintegrowanej powłoki, zarówno z pakietów redystrybucyjnych [Microsoft Visual Studio Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Przed uzyskaniem dostępu do izolowanych i zintegrowanych pakietów redystrybucyjnych powłoki zostanie wyświetlony monit o wypełnienie krótkiej ankiety klienta.  Po wypełnieniu ankiety nastąpi przekierowanie do strony programu Visual Studio Connect z linkami pobierania pakietu redystrybucyjnego.  Linki do pobrania można znaleźć w kolejnych odwiedzinach w witrynie programu Visual Studio Connect w obszarze **programy &#124; kartę zintegrowane i izolowane powłoka programu Visual studio 2015** .  
  
 W przypadku zainstalowania zintegrowanej aplikacji powłoki na tym samym komputerze co pełna wersja programu Visual Studio składniki aplikacji zostaną zintegrowane bezpośrednio z Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funkcje w zintegrowanej powłoce  
  
|Obszar funkcji|Cechy|  
|-|-|  
|Obsługa języków|-   Brak|  
|IDE|<ul><li>Ustawienia<br /><br /> <ul><li>Utwórz ustawienia</li><li>Importowanie i eksportowanie ustawień</li><li>Resetuj ustawienia</li></ul></li><li>Integracja z **zestawem narzędzi**</li><li>Integracja **Lista zadań**</li><li>Pomoc dotycząca integracji</li><li>**Opcje** — okno dialogowe</li><li>Zarządzanie czcionkami i kolorami</li><li>Okno **danych wyjściowych**</li><li>Okno **polecenia**</li><li>Zarządzanie oknem</li><li>Polecenia, menu i powiązania klawiszy</li><li>Środowisko uruchomieniowe języka specyficznego dla domeny (DSL)</li></ul>|  
|System projektu i typy projektów|— Rozwiązania i foldery rozwiązań<br />— Rozwiązanie Configuration Manager<br />-Zarządzanie elementami<br />— Rozwiązania z pojedynczym projektem i projektem<br />-Projektant aplikacji (uproszczone właściwości projektu)<br />-Dodaj odwołanie sieci Web<br />-Dodaj odwołanie do usługi<br />-Jeden projekt<br />— Typy projektów witryny sieci Web<br />— Projekty aplikacji sieci Web|  
|Kompilacja|-Niestandardowe kroki kompilacji w środowisku IDE<br />— Wstępna kompilacja dla ochrony własności intelektualnej (IP)<br />-Podpisywanie kodu<br />     MSBuild|  
|Edytor|-Narzędzia do przeglądania kodu (ujednolicone wyszukiwanie, definicja źródła, dziedziczenie)<br />-Nawigacja po kodzie<br />— Technologia IntelliSense<br />- SmartTags<br />— Refaktoryzacja<br />-Łatwa lista<br />— Filtrowanie funkcji IntelliSense<br />-   Okno **definicji kodu**|  
|Projektant|— Projektant Windows Presentation Foundation<br />-Projektant formularzy systemu Windows<br />— Projektant sieci Web i Edytor HTML|  
|Dane|-   **Eksplorator serwera** (uproszczone: tylko dane). Patrz Uwaga 1.<br />-   Okno **źródeł danych**<br />-Pełen zestaw kontrolek danych<br />— Edytor XML<br />— Powiązanie danych z lokalnym źródłem danych (. MDF lub. MDB<br />— Powiąż dane z obiektem<br />-Powiązanie danych z usługą sieci Web<br />-Powiązanie danych z lokalnym serwerem baz danych<br />-Powiązanie danych z serwerem zdalnej bazy danych<br />-DDL Tools dla danych zdalnych<br />-   Rozszerzalność **Eksplorator serwera** ( [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] przykłady)|  
|Debuger|— Debugowanie lokalne. Patrz Uwaga 2.<br />Debugowanie zarządzane<br />— Debugowanie lokalne<br />— Dołącz do procesu lokalnego<br />— Dołącz do procesu zdalnego<br />-Anonimowy delegat<br />-Domeny aplikacji<br />-Debugowanie ASPX<br />-Atrybuty<br />-Break podczas wykonywania funkcji Func-eval<br />-Punkty przerwania<br />-Ograniczenia punktów przerwania<br />-Stosu wywołań<br />-   Okno **polecenia**<br />— Debugowanie między wątkami<br />— Porady dotyczące danych<br />-Wizualizator danych<br />— Obsługa debugera dla asystentów zarządzanego debugowania (MDA)<br />-Debuger obsługujący funkcję przesyłania dalej typów<br />-DTEEvents obsługa OTB<br />-JMC stepper<br />-Debuger AppID test (DBGCLR)<br />-Debuger — profil<br />— Narzędzia i opcje debugera<br />-Iterator debugowania<br />-Obliczanie wyrażenia czasu projektowania<br />— Ewaluatora wyrażeń w języku C#<br />-Demontaż<br />-Edytuj i Kontynuuj<br />— Okna ewaluatora wyrażeń (czujka, zmienne lokalne, autouzupełniania)<br />-Pomocnik wyjątków<br />-Wyjątki<br />-Wykonywanie<br />-Typy ogólne<br />— Uzyskiwanie właściwego źródła<br />-HPC/Debugowanie klastra<br />-Zintegrowane debugowanie wielu języków<br />— Debugowanie międzyoperacyjności<br />Debugowanie just in Time<br />— Debugowanie lokalne<br />Debugowanie zarządzane<br />— Kontrola ręczna (okno procesów)<br />- Pamięć<br />— Obsługa minizrzutu<br />-Moduły<br />-Debugowanie wieloprocesowe<br />— Debugowanie natywne<br />-Nowa obsługa aparatu debugowania<br />Debugowanie kodu zoptymalizowane<br />-Wyjściowe filtrowanie systemu Windows<br />-Proces hostingu dla debugowania zarządzanego<br />-Procesy<br />-QuickWatch<br />-Rejestruje<br />-Rejestruje w stosie<br />-Debugowanie zdalne<br />-Wartości zwracane<br />-Debugowanie skryptu<br />-Obsługa usługi źródłowej<br />-Zabezpieczenia<br />Obok siebie<br />— SQL<br />— Serwer symboli<br />-Punkty śledzenia<br />-Thread<br />— Wizualizacje<br />-Extensible Stylesheet Language Transformations (XSLT) Debugger|  
|64 — obsługa bitów|-64-bitowe debugowanie dla kodu zarządzanego i natywnego, wszystkie języki<br />-x64 Native support|  
|Kontrola kodu źródłowego (SCC)|-Podstawowa integracja SCC. Patrz adnotacja 3.<br />— Weryfikacja narzędzi i opcji|  
|Rozszerzalność|-Korzystanie ze składników pakietów VSPackage i MEF|  
  
## <a name="notes"></a>Uwagi  
  
#### <a name="1-data-tools"></a>1. narzędzia danych  
 Zintegrowana powłoka obejmuje narzędzia do tworzenia baz danych, takie jak obsługa rozszerzalności danych i uproszczone **Eksplorator rozwiązań**. Jednak SQL Server Express, SQL Reporting i Crystal Reports nie znajdują się w zintegrowanej powłoce.  
  
#### <a name="2-debugging-support"></a>2. obsługa debugowania  
 Zintegrowana powłoka obejmuje ten sam aparat debugowania, który jest dołączony do wersji społeczności programu Visual Studio. Aparat debugowania zawiera wspólny debuger dla kodu zarządzanego, a także powiązane funkcje, takie jak uruchamianie, dołączanie, Ustawianie punktu przerwania, Edycja i kontynuowanie oraz inne. Jednak aparat debugowania nie obsługuje debugowania bazy danych SQL Server.  
  
 Chociaż obsługa debugowania natywnego jest zawarta w podstawowym pakiecie debugera, nie można jej zwiększyć na potrzeby obsługi dodatkowych języków.  
  
#### <a name="3-source-code-control-integration"></a>3. Integracja kontroli kodu źródłowego  
 Zintegrowana powłoka udostępnia interfejsy API służące do implementowania kontroli kodu źródłowego (SCC) i udostępniania wspólnych składników integracji kontroli źródła opartych na MSSCCI.  
  
 Chociaż integracja SCC nie jest regularną funkcją wersji Pro programu Visual Studio, integracja SCC jest dostępna w zintegrowanej powłoce.  
  
#### <a name="4-build-support"></a>4. Obsługa kompilacji  
 Zintegrowana powłoka zapewnia obsługę kompilacji. Informacje o kompilacjach można znaleźć w [dokumentacji programu MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funkcje nieuwzględnione w zintegrowanej powłoce  
 Poniżej znajduje się lista funkcji, które nie są uwzględnione w zintegrowanej powłoce:  
  
- Projektant klas  
  
- PreEmptive Protection — Dotfuscator  
  
- Funkcje językowe  
  
- VSHost  
  
- W zintegrowanej powłoce nie ma żadnych języków programu Visual Studio ani skojarzonych z nimi szablonów projektów ani szablonów elementów projektu. Nie są uwzględniane żadne implementacje innych funkcji, na przykład Visual Basic fragmenty kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie programu Visual Studio — omówienie](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
