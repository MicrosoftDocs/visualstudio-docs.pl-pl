---
title: Uaktualnianie kodowanych testów interfejsu użytkownika
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58bfe0a2a6c337081ebb96464a701decb73cc022
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080699"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Aktualizowanie kodowanych testów interfejsu użytkownika z Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testowanie projektów zawierających kodowane testy interfejsu użytkownika, które zostały utworzone w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 dyskretnie naprawiane po otwarciu w programie Visual Studio 2012. Jeśli projekty testowe są zaewidencjonowane do kontroli źródła, pliki projektu są wyewidencjonowane dla tej naprawy. Po naprawieniu te projekty zawierające kodowanego interfejsu użytkownika testy mogą testowe, a następnie można używać zarówno w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1 i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Wymagania**

- Visual Studio Enterprise

> [!NOTE]
>  Visual Studio zawiera więcej niż jeden typ projektu testowego. Jeśli tworzysz nowy kodowany test interfejsu użytkownika, zostanie utworzony w typu projektu kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [uaktualnianie testów ze starszych wersji programu Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
>  [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Projekty testowe, które zawiera kodowane testy interfejsu użytkownika musi zostać zrekompilowany, po otwarciu projektu testowego w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] side-by-side przy użyciu [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
>  Jeśli projekt testowy, który został utworzony w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i zawiera tylko testów jednostkowych jest otwarty w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodowane testy interfejsu użytkownika nie można dodać do niego. Podobnie nie można dodać kodowanego testu interfejsu użytkownika do projektu testu jednostkowego, który został utworzony w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problemy ze zgodnością między Visual Studio 2010 i Visual Studio 2012
 Poniższa lista zawiera problemy, które należy wiedzieć podczas migrowania kodowane testy interfejsu użytkownika między [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
>  Jest to znany problem dotyczący odwołania w projektach testów interfejsu użytkownika kodowany nie są wyświetlane w Eksploratorze rozwiązań. Aby uzyskać więcej informacji, zobacz plik ReadMe dołączonym [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nośnika instalacyjnego.

|Kodowany interfejs użytkownika funkcji|Problem|Rozwiązanie|
|----------------------------|-----------|--------------|
|Testowanie interfejsu użytkownika programu Silverlight nie jest obsługiwane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja zakończy się niepowodzeniem**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 i ma utworzone kodowanego projektów testów interfejsu użytkownika dla aplikacji Silverlight, te projekty nie można otworzyć w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Zalecamy Zarządzanie te projekty w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] tylko Feature Pack 2.|
|Testowanie interfejsu użytkownika programu Firefox nie jest obsługiwane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja zostanie wykonana pomyślnie, przebieg testu zakończy się niepowodzeniem.**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 i ma utworzone kodowanego projektów testów interfejsu użytkownika dla aplikacji sieci web w przeglądarce Firefox, te projekty nie można otworzyć w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Zalecamy Zarządzanie te projekty w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] tylko Feature Pack 2.|
|Nowy kod interfejsu użytkownika testowania interfejsów API zostały dodane w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Kompilacja zakończy się niepowodzeniem**<br /><br /> Jeśli utworzysz kodowanych testów interfejsu użytkownika przy użyciu nowego interfejsu użytkownika testowanie interfejsu API w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nie można otworzyć te projekty w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Należy zarządzać projektami za pomocą nowego interfejsu API [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] tylko.|
|W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], odwołania zostały dodane wewnątrz instrukcji "Wybierz" w pliku csproj jest niewielki. W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], firma Microsoft jest używany plik elementów docelowych opinii uwzględniał odwołania kodowanego interfejsu użytkownika zestawu testowego.|W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodowanego testu interfejsu użytkownika nie można dodać do projektu testowego utworzone w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (lub z dodatkiem SP1), nie zawierała kodowanego testu interfejsu użytkownika.<br /><br /> Proces naprawy dodaje plik elementów docelowych i instrukcja wybierz. Jeśli kodowanego testu interfejsu użytkownika nie znajduje się w projekcie testu, projekt zostanie oznaczony jako naprawione i odpowiednie odwołania nie zostaną dodane przy dodawaniu kodowanego testu interfejsu użytkownika w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Musisz utworzyć nowy projekt testowy do tego samego rozwiązania przy użyciu [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] i Dodaj nowego kodowanego testu interfejsu użytkownika. Alternatywnie można dodać kodowanych testów interfejsu użytkownika do projektu testu w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1 i otwarcie projektu w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 z dodatkiem SP1 Update
 Aktualizacja [!INCLUDE[vs2010](../includes/vs2010-md.md)] z obsługą zgodności dla programu Visual Studio 2012 i Windows 8 z dodatkiem SP1 jest dostępny do pobrania na [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) i zaktualizuj również jako programu Visual Studio.

 Po zastosowaniu aktualizacji, następujące [!INCLUDE[vs2010](../includes/vs2010-md.md)] funkcji narzędzia w kodowanych testów interfejsu użytkownika zostały udoskonalone specjalnie dla systemu Windows 8 z dodatkiem SP1:

- Kodowanego testu interfejsu użytkownika dla Microsoft określa oparte na programie .NET Framework 4.5 Windows Presentation Foundation (WPF) można uruchomić na komputerze z systemem Windows 8.

- Na komputerze z systemem Windows 8, można uruchomić kodowanego testu interfejsu użytkownika dla 64-bitowych (x 64) Internet Explorer 10.

  Aktualizacja również rozwiązuje następujące problemy:

- **Pokrycie kodu:** Brak możliwości, otwórz plik pokrycia kodu (.coverage), który jest tworzony przez program Visual Studio 2012 w [!INCLUDE[vs2010](../includes/vs2010-md.md)] z dodatkiem SP1.

- **Artefakty opuszczone testów:** Twój zespół ma artefakt testu, który jest przypisany do nieprawidłowego użytkownika w Team Foundation Server (TFS) 2010. Na przykład użytkownik opuścił firmę, ale nadal ma przypadek testowy, który jest przypisany do niego. Można uaktualnić modelu obiektów TFS 2010 do wersji TFS 2012. Możesz użyć [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010, aby nawiązać połączenie z uaktualnionego serwera TFS. Nie jest możliwe do artefaktów testowych można przypisać do użytkowników TFS, używając [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Testowanie obciążenia:** Możesz uruchomić test obciążenia wraz z sieci typu innego niż profil sieci lokalnej (LAN) na komputerze, to jest uruchomiony system Windows 8, sterownik emulatora sieci powoduje awarię systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [2736182 artykułu KB](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Zobacz też
 [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [uaktualnianie testów ze starszych wersji programu Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [generowania Kodowany Test interfejsu użytkownika z istniejącego nagrania akcji](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
