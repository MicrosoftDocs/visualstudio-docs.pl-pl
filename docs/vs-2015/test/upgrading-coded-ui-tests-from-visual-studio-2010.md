---
title: Uaktualnianie kodowanych testów interfejsu użytkownika
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1db5e653889f75931916c44de22e545415b53a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657249"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Aktualizowanie kodowanych testów interfejsu użytkownika z Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty testowe zawierające kodowane testy interfejsu użytkownika, które zostały utworzone w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, są dyskretnie naprawiane po otwarciu w programie Visual Studio 2012. Jeśli projekty testowe są sprawdzane w kontroli źródła, pliki projektu są wyewidencjonowane dla tej naprawy. Po naprawieniu te projekty testowe zawierające kodowane testy interfejsu użytkownika mogą być używane zarówno w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, jak i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Requirements**

- Visual Studio Enterprise

> [!NOTE]
> Program Visual Studio zawiera więcej niż jeden typ projektu testowego. W przypadku utworzenia nowego kodowanego testu interfejsu użytkownika zostanie on utworzony w typie projektu kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [uaktualnianie testów ze starszych wersji programu Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] projekty testowe, które zawierają kodowane testy interfejsu użytkownika, muszą zostać odbudowane po otwarciu projektu testowego w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] obok [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
> Gdy projekt testowy, który został utworzony w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i zawiera tylko testy jednostkowe, jest otwarty w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nie można dodać do niego kodowanych testów interfejsu użytkownika. Podobnie nie można dodać kodowanego testu interfejsu użytkownika do projektu testu jednostkowego, który został utworzony w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problemy ze zgodnością między programami Visual Studio 2010 i Visual Studio 2012
 W poniższej tabeli wymieniono problemy, które należy wziąć pod uwagę podczas migrowania kodowanych testów interfejsu użytkownika między [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
> Istnieje znany problem dotyczący odwołań w kodowanych projektach testów interfejsu użytkownika, które nie pojawiają się w Eksplorator rozwiązań. Aby uzyskać więcej informacji, zobacz plik Readme zawarty na nośniku instalacyjnym programu [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

|Kodowane funkcje interfejsu użytkownika|Problem|Rozwiązanie|
|----------------------------|-----------|--------------|
|Testowanie interfejsu użytkownika programu Silverlight nie jest obsługiwane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja zakończy się niepowodzeniem**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 i utworzono projekty kodowanego testu interfejsu użytkownika dla aplikacji Silverlight, te projekty nie mogą być otwierane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Zalecamy zarządzanie tymi projektami tylko [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|Testowanie interfejsu użytkownika w przeglądarce Firefox nie jest obsługiwane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja powiedzie się, przebieg testowy zakończy się niepowodzeniem**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 i utworzono projekty kodowanego testu interfejsu użytkownika dla aplikacji sieci Web w programie Firefox, te projekty nie mogą być otwierane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Zalecamy zarządzanie tymi projektami tylko [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|Dodano nowe interfejsy API testowania kodu interfejsu użytkownika w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja zakończy się niepowodzeniem**<br /><br /> W przypadku tworzenia kodowanych testów interfejsu użytkownika przy użyciu nowego interfejsu API testowania interfejsu użytkownika w programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projekty te nie mogą być otwierane w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Projekty używające nowego interfejsu API powinny być zarządzane wyłącznie w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|
|W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] odwołania zostały dodane wewnątrz instrukcji "Select" w pliku csproj. W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] używamy pliku celów opinii, aby uwzględnić odwołania do zestawu kodowanych testów interfejsu użytkownika.|W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nie można dodać kodowanego testu interfejsu użytkownika do projektu testowego utworzonego w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (lub z dodatkiem SP1), który nie zawiera kodowanego testu interfejsu użytkownika.<br /><br /> Proces naprawy dodaje plik targets i instrukcję SELECT. Jeśli kodowany test interfejsu użytkownika nie znajduje się w projekcie testowym, projekt zostanie oznaczony jako naprawiony, a odpowiednie odwołania nie zostaną dodane podczas dodawania kodowanego testu interfejsu użytkownika w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Konieczne będzie utworzenie nowego projektu testowego w tym samym rozwiązaniu przy użyciu [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] i dodanie do niego nowego kodowanego testu interfejsu użytkownika. Alternatywnie można dodać kodowane testy interfejsu użytkownika do projektu testowego w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 i otworzyć ten projekt w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a>Aktualizacja programu Visual Studio 2010 z dodatkiem SP1
 Aktualizacja [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 z obsługą zgodności dla programu Visual Studio 2012 i systemu Windows 8 jest dostępna do pobrania w [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) , a także jako aktualizacja programu Visual Studio.

 Po zastosowaniu aktualizacji w systemie Windows 8 Ulepszono następujące funkcje narzędzia kodowanego testu interfejsu użytkownika [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1:

- Można uruchomić kodowany test interfejsu użytkownika dla kontrolek Windows Presentation Foundation (WPF) w Microsoft .NET Framework 4,5 na komputerze z systemem Windows 8.

- Można uruchomić kodowany test interfejsu użytkownika dla 64-bitowej (x64) programu Internet Explorer 10 na komputerze z systemem Windows 8.

  Aktualizacja zawiera również poprawki dotyczące następujących problemów:

- **Pokrycie kodu:** Nie można otworzyć pliku pokrycia kodu (pokrycie), który jest tworzony przez program Visual Studio 2012 w [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Opuszczone artefakty testowe:** Twój zespół ma artefakt testowy, który jest przypisany do nieprawidłowego użytkownika w Team Foundation Server (TFS) 2010. Na przykład użytkownik opuścił firmę, ale nadal ma przypisany przypadek testowy. Uaktualniasz TFS 2010 do TFS 2012. Do nawiązania połączenia z uaktualnionym serwerem TFS służy [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010. Nie można przypisać artefaktu testowego do żadnych użytkowników TFS przy użyciu [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Testowanie obciążenia:** Po uruchomieniu testu obciążenia razem z typem sieci innym niż profil sieci lokalnej (LAN) na komputerze z systemem Windows 8, sterownik emulatora sieciowego powoduje awarię systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [artykuł w bazie wiedzy 2736182](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Zobacz też
 Przenoszenie [, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [uaktualnianie testów ze starszych wersji programu Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [generującego kodowany test interfejsu użytkownika z istniejącego rejestrowania akcji](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [ Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
