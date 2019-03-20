---
title: Okno dialogowe wymagania wstępne | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 593db9fe2f460229cfdd4c241124ef8270448094
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194661"
---
# <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
To okno dialogowe określa, które wstępnie wymagane składniki są zainstalowane, jak są zainstalowane i jakim porządku zainstalowane są pakiety.  
  
 Aby otworzyć to okno dialogowe, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **publikowania** kartę. Na **Publikuj** kliknij **wymagania wstępne**. W przypadku projektów instalacji na **projektu** menu, kliknij przycisk **właściwości**. Gdy **stron właściwości** pojawi się okno dialogowe, kliknij przycisk **wymagania wstępne**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
  
|Element|Opis|  
|-------------|-----------------|  
|**Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**|Zawiera wstępnie wymagane składniki w program instalacyjny aplikacji (Setup.exe), dzięki czemu zostaną one zainstalowane przed aplikacją, w kolejności zależności. Domyślnie ta opcja jest zaznaczona. Jeśli nie jest zaznaczone, Setup.exe nie zostanie utworzony.|  
|**Wybierz wstępnie wymagane składniki do zainstalowania**|Określa, czy należy zainstalować składniki, takie jak [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports i tak dalej.<br /><br /> Na przykład przez zaznaczenie pola wyboru obok pozycji **programu SQL Server 2005 Express Edition z dodatkiem SP2**, należy określić, że program instalacyjny sprawdzi, czy ten składnik jest zainstalowany na komputerze docelowym i zainstaluj go, jeśli nie jest już zainstalowany.<br /><br /> Aby uzyskać szczegółowe informacje dotyczące każdego pakietu wstępnie wymaganych składników zobacz informacje o wymaganiach wstępnych tabeli w dalszej części tego tematu.|  
|**Sprawdź Microsoft Update, aby uzyskać więcej składników redystrybucyjnych**|Kliknięcie tego linku spowoduje przejście do [program inicjujący pakietów do rozpowszechniania składników](http://go.microsoft.com/fwlink/?LinkId=208835) witryny sieci Web, aby wyszukać aktualizacje.|  
|**Pobierz wstępnie wymagane składniki z witryny dostawcy składników**|Określa, że wstępnie wymagane składniki będą instalowane z witryny sieci Web dostawcy. Jest to opcja domyślna.|  
|**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**|Określa, że wstępnie wymagane składniki będą instalowane z tej samej lokalizacji co aplikacja. To kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|  
|**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Określa, że wstępnie wymagane składniki będą instalowane z wybranej lokalizacji. Możesz użyć **Przeglądaj** przycisk, aby wybrać lokalizację.|  
  
## <a name="prerequisites-information"></a>Informacje o wymaganiach wstępnych  
 Wstępnie wymagane składniki, które pojawiają się w **wymagania wstępne** okno dialogowe mogą się różnić od tych z poniższej listy. Wstępnie wymagane pakiety wymienione w **wstępnie wymagane składniki, okno dialogowe** są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni później platformę docelową projektu, trzeba będzie wybrać wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.  
  
|Element|Opis|  
|-------------|-----------------|  
|**.NET Framework 3.5 SP1**|Ten pakiet zainstaluje następujące:<br /><br /> — Program .NET framework w wersji 2.0, 3.0 i 3.5.<br />— Obsługuje dla wszystkich wersji .NET Framework na 32-bitowych (x86) i (x64) 64-bitowych systemów operacyjnych.<br />-Pakiety językowe dla każdej wersji .NET Framework, która jest instalowana z pakietem.<br />-Dodatki service Pack dla programu .NET Framework 2.0 i 3.0.<br /><br /> .NET framework 3.0 jest dołączony do Windows Vista i programu .NET Framework 3.5 jest dołączony [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. .NET framework 3.5 jest wymagany dla wszystkich projektów Visual Basic i Visual C#, które są kompilowane dla 32-bitowych systemach operacyjnych i dla którego platforma docelowa jest ustawiona na **.NET Framework 3.5**, a dla projektów języka Visual Basic i Visual C# skompilować dla 64-bitowych systemach operacyjnych. (IA64 nie jest obsługiwany.) Należy pamiętać, że projekty języka Visual Basic i Visual C# są kompilowane dla dowolnej architektury Procesora domyślnie. Aby uzyskać więcej informacji, zobacz [Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md), [Redystrybucja środowiska .NET Framework](http://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287), i [wdrażanie wymagania wstępne dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Domyślnie ten element jest wybrany.|  
|**Profil klienta programu .NET framework 3.5 z dodatkiem SP1**|Profil klienta .NET Framework jest podzestawem pełnego .NET Framework 3.5 SP1 przeznaczonego dla aplikacji klienckich. Zawiera uspójniony podzbiór Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) i funkcji ClickOnce. Umożliwia to szybkie wdrażanie scenariuszy dla WPF, Windows Forms, WCF i aplikacji konsoli przeznaczonych dla profilu klienta .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft .NET Framework 4 (x86 i x64)**|Ten pakiet instaluje .NET Framework 4 dla x86 i x64 64.<br /><br /> Aby uzyskać więcej informacji, zobacz [Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md), [Redystrybucja środowiska .NET Framework](http://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287), i [wdrażanie wymagania wstępne dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Domyślnie ten element jest wybrany.|  
|**Microsoft .NET Framework 4 Client Profile (x86 i x64)**|.NET Framework 4 Client Profile jest podzestawem pełnego .NET Framework 4, który jest przeznaczony dla aplikacji klienckich. Zawiera uspójniony podzbiór Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) i funkcji ClickOnce. Umożliwia to szybkie wdrażanie scenariuszy dla WPF, Windows Forms i aplikacji konsoli przeznaczonych dla profilu klienta .NET Framework 4. Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft Office 2007 podstawowe zestawy międzyoperacyjne**|Ten pakiet instaluje podstawowe zestawy międzyoperacyjne dla 2007 produktów Microsoft Office. Podstawowy zestaw międzyoperacyjny umożliwia kodu zarządzanego do interakcji z modelem obiektów opartym na modelu COM aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](http://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|  
|**Microsoft Visual Basic PowerPacks version 10.0**|Pakiety Power Pack to dodatki, formanty, składniki i narzędzia do pomocy w tworzeniu aplikacji języka Visual Basic. Ta wersja zawiera <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik, który pozwala na drukowanie zawartości formularza Windows oraz biblioteki zgodności drukarki, która umożliwia uruchomienie niemodyfikowanego kodu języka Visual Basic 6.0 drukarki.|  
|**Microsoft Visual F# środowiska uruchomieniowego dla platformy .NET w wersji 2.0**|Ten pakiet instaluje wizualizacji F# bibliotek środowiska uruchomieniowego dla x86 i x64 systemów operacyjnych, które zapewniają obsługę programowania funkcjonalnego, a także tradycyjnego programowania obiektowego oraz imperatywnego (proceduralnego). Ten pakiet musi być zainstalowany, jeżeli aplikacja lub jej części składowe, została utworzona w elemencie wizualnym F# i .NET Framework 2.0, .NET Framework 3.0 lub .NET Framework 3.5.<br /><br /> Aby uzyskać więcej informacji, zobacz [ F# Language Reference](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual F# środowiska uruchomieniowego dla platformy .NET 4.0**|Ten pakiet instaluje wizualizacji F# bibliotek środowiska uruchomieniowego dla x86 i x64 systemów operacyjnych, które zapewniają obsługę programowania funkcjonalnego, a także tradycyjnego programowania obiektowego oraz imperatywnego (proceduralnego). Ten pakiet musi być zainstalowany, jeżeli aplikacja lub jej części składowe, została utworzona w elemencie wizualnym F# i .NET Framework 4.<br /><br /> Aby uzyskać więcej informacji, zobacz [ F# Language Reference](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual Studio 2010 Report Viewer**|Ten pakiet zainstaluje formanty podglądu raportu, używane do dodawania danych raportowania do aplikacji ASP.NET i Windows Forms.|  
|**Microsoft Visual Studio 2010 dla Office Runtime (x86 i x64)**|Narzędzia Office developer tools w programie Visual Studio oferuje łatwe w użyciu, zintegrowane narzędzia do tworzenia rozwiązań biznesowych za pomocą programu Microsoft Office. Można tworzyć zarządzane, inteligentne rozwiązania klienckie, które korzystają z aplikacji pakietu Office jako interfejsu użytkownika. Narzędzia te umożliwiają programistom tworzenie bezpiecznych rozwiązań, które są łatwe do wdrożenia i obsługi.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Publikowanie rozwiązań pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x86)**|Ten pakiet zainstaluje Microsoft SQL Server 2005 Express Edition SP2, aplikację baza danych, która opiera się na [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]. SQL Server Express jest zamiennikiem dla programu Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express jest bezpłatny i może być rozprowadzany (postanowieniom Umowy) i funkcjonuje jako baza danych klienta i podstawowa baza danych serwera. Jest taka sama jak SQL Server 2005, z wyjątkiem następujących różnic:<br /><br /> -Brak obsługi funkcji przedsiębiorstwa.<br />-Ograniczone do jednego Procesora.<br />-limit pamięci 1 gigabajt (GB) dla puli buforów.<br />-Maksymalny rozmiar 4 GB dla baz danych.|  
|**SQL Server 2008 Express**|Ten pakiet zainstaluje Microsoft SQL Server 2008 Express, bezpłatna wersja programu Microsoft SQL Server 2008, idealną bazę danych dla małych sieci web, serwera lub aplikacji klasycznych. Może służyć do swobodnego rozwoju i produkcji. Bezpłatna rejestracja jest wymagana do dystrybucji programu SQL Server 2008 Express z aplikacją.<br /><br /> Program inicjujący zachowuje jest następująca:<br /><br /> — Jeśli komputer ma już program SQL Server 2008 Express lub nowszy, komputer pozostaje w programie SQL Server 2008 Express lub nowszej.<br />— Jeśli komputer nie ma dowolnej wersji programu SQL Server 2008 Express lub nowszej, pakiet instaluje najnowszą wersję programu SQL Server 2008 Express z dodatkiem SP1.<br /><br /> Aby dowiedzieć się więcej na temat programu SQL Server 2008 Express, odwiedź stronę [ http://go.microsoft.com/fwlink/?LinkId=183586 ](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Biblioteki Visual C++ 2010 Runtime (IA64)**|Ten pakiet instaluje biblioteki Visual C++ środowiska wykonawczego dla architektury Itanium, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Biblioteki Visual C++ 2010 Runtime (x64)**|Ten pakiet instaluje biblioteki uruchomieniowe Visual C++ x64 systemów, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Biblioteki Visual C++ 2010 Runtime (x86)**|Ten pakiet instaluje biblioteki uruchomieniowe Visual C++ dla x86 systemów, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Instalator Windows 3.1**|Ten pakiet zainstaluje Instalatora systemu Microsoft Windows, w wersji redystrybucyjnej 3.1, który umożliwia instalację projektów instalacji Instalatora Windows. Jest preinstalowany w systemie Windows Server 2003 z dodatkiem SP1 lub nowszy.<br /><br /> Domyślnie ten element jest wybrany.|  
|**Instalator Windows 4.5**|Ten pakiet zainstaluje Instalatora systemu Microsoft Windows, w wersji redystrybucyjnej 4.5, który umożliwia instalację projektów instalacji Instalatora Windows.|  
  
## <a name="see-also"></a>Zobacz też  
 [Strona publikowania, Projektant projektu](../../ide/reference/publish-page-project-designer.md)   
 [Wymagania wstępne wdrożenia aplikacji](../../deployment/application-deployment-prerequisites.md)   
 [Redystrybucja środowiska .NET Framework](http://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287)   
 [Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Wielowersyjność kodu w programie Visual Studio ― przegląd](../../ide/visual-studio-multi-targeting-overview.md)
