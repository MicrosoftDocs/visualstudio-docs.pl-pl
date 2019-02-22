---
title: Najlepsze rozwiązania programistyczne dla modelu COM, VSTO i VBA dodatków pakietu Office
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b81dec69d27cc32fa5e6848d358049d8b8e2c04e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643577"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Najlepsze rozwiązania programistyczne dla modelu COM, VSTO i VBA dodatków pakietu Office
  Jeśli tworzysz COM, VSTO i VBA dodatków pakietu Office, postępuj zgodnie z najlepszych rozwiązań programistycznych opisanych w tym artykule.   Ułatwi to zapewnienie:

-  Zgodność dodatków między różnymi wersjami i wdrożenia pakietu Office.
-  Złożoności wdrażania dodatku dla użytkowników i administratorów IT.
-  Nie występują niezamierzone instalacji lub środowisko uruchomieniowe błędów dodatku.

>Uwaga: Za pomocą [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) przygotować swoje COM, VSTO i VBA dodatku Store Windows nie jest obsługiwane. COM, VSTO i VBA dodatki nie mogą być dystrybuowane w Windows Store lub Store pakietu Office.

## <a name="do-not-check-for-office-during-installation"></a>Nie sprawdzaj Office podczas instalacji
 Nie zaleca się posiadanie dodatku wykryć, czy pakietu Office jest zainstalowana podczas procesu instalacji dodatku. Jeśli nie zainstalowano pakietu Office, można zainstalować dodatku, a użytkownik będzie mógł uzyskać do niego dostęp, po zainstalowaniu pakietu Office.

## <a name="use-embedded-interop-types-nopia"></a>Użyj osadzone typy międzyoperacyjne (NoPIA)
Jeśli Twoje rozwiązanie używa programu .NET 4.0 lub nowszym, użyj osadzone typy współdziałania (NoPIA) zamiast w zależności od pakietu Office podstawowego Interop zestawy MIĘDZYOPERACYJNE pakiet redystrybucyjny. Za pomocą typu osadzania zmniejsza rozmiar instalacji rozwiązania i gwarantuje zgodności w przyszłości. Pakiet Office 2010 został najnowszej wersji pakietu Office, dostarczanej PIA do dystrybucji. Aby uzyskać więcej informacji, zobacz [instruktażu: Osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) i [równoważność typów i osadzone typy międzyoperacyjne](/windows/uwp/porting/desktop-to-uwp-root).

Jeśli rozwiązanie używa starszej wersji oprogramowania .NET, zaleca się zaktualizowanie rozwiązania na platformie .NET 4.0 lub nowszy. Przy użyciu platformy .NET 4.0 lub nowszy zmniejsza wymagania wstępne dotyczące środowiska uruchomieniowego, w nowszych wersjach systemu Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Należy unikać w zależności od określonej wersji pakietu Office
Jeśli rozwiązanie używa funkcji, która jest dostępna tylko w nowszej wersji pakietu Office, sprawdź, czy funkcja istnieje (Jeśli to możliwe, na poziomie funkcji) w czasie wykonywania (na przykład za pomocą wyjątek Obsługa lub Sprawdzanie wersji). Sprawdzanie poprawności co najmniej wersji zamiast określonych wersji, przy użyciu obsługiwanych interfejsów API w modelu obiektów, takich jak [właściwość Application.Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nie zaleca się że polegasz binarne metadanych, ścieżek instalacji i kluczy rejestru pakietu Office, ponieważ te można zmieniać, instalacje, środowisk i wersji.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Włącz użycie pakietu Office zarówno 32-bitowych i 64-bitowych
Domyślny element docelowy kompilacji powinien obsługiwać zarówno (x86) 32-bitowych, jak i (x64) 64-bitowych, chyba że rozwiązanie jest zależna od bibliotek, które są dostępne tylko dla określonej liczby bitów. 64-bitowej wersji pakietu Office, zwiększa się w przyjęciu, szczególnie w środowiskach danych big data. Wspierające zarówno 32-bitowych i 64-bitowych ułatwia użytkownikom przejścia między 32-bitowych i 64-bitowej wersji pakietu Office.

Podczas pisania kodu VBA, bezpieczne 64-bitowych użyj instrukcji deklarowania i przekonwertować zmienne zgodnie z potrzebami. Dodatkowo należy upewnić się, że dokumenty mogą być współużytkowane między korzystania z 32-bitowy lub 64-bitowej wersji pakietu Office, zapewniając kodu dla każdej liczby bitów. Aby uzyskać więcej informacji, zobacz [64-bitowych języka Visual Basic for applications overview](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Ograniczona obsługa środowisk
Rozwiązania nie powinien wymagać uprawnień podniesienia uprawnień konta użytkownika lub administratora. Ponadto rozwiązania nie powinno zależeć od Ustawianie lub zmienianie:

- Bieżący katalog roboczy.
- Katalogi załadowanie biblioteki DLL.
- Zmienna ścieżki.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Zapisz zmiany lokalizacji danych udostępnionych i ustawienia
Jeśli to rozwiązanie składa się z dodatku i proces, który znajduje się poza pakietu Office, nie używaj folder dane aplikacji użytkownika lub rejestru do programu exchange, dane lub ustawienia między dodatek i proces zewnętrzny. Zamiast tego należy wziąć pod uwagę przy użyciu folder tymczasowy użytkownika, folder dokumenty lub katalog instalacyjny tego rozwiązania.

## <a name="increment-the-version-number-with-each-update"></a>Zwiększ numer wersji w każdej aktualizacji
Ustaw numer wersji plików binarnych w swoim rozwiązaniu i zwiększenia przy każdej aktualizacji. Ułatwi służący do identyfikowania zmian między wersjami i oceny zgodności.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Podaj oświadczenia dotyczące pomocy technicznej dla najnowszej wersji pakietu Office
Klienci są zadawanie niezależnym dostawcom oprogramowania w celu zapewnienia pomocy technicznej instrukcje dotyczące ich COM, VSTO i VBA dodatków działających w pakiecie Office. Listę klientów obsługi jawnych instrukcji pomaga przy użyciu usługi Office 365 ProPlus gotowości narzędzia informacje o pomocy technicznej Twojej.

Aby zapewnić oświadczenia dotyczące pomocy technicznej dla aplikacji klienckich pakietu Office (na przykład Word lub Excel), należy najpierw sprawdzić dodatków uruchamiane w bieżącej wersji pakietu Office, a następnie przekazać do udostępnienia aktualizacji, jeśli dodatek przerywa w przyszłej wersji. Nie masz przetestować dodatków, gdy firma Microsoft publikuje nową kompilację lub aktualizację pakietu Office. Microsoft, zmieniają się rzadko platform rozszerzalności modelu COM, VSTO i VBA w pakiecie Office, a te zmiany będzie dobrze udokumentowane.

>Ważne: Firma Microsoft udostępnia listę obsługiwanych dodatki dla raportów gotowości i informacje kontaktowe niezależnego dostawcy oprogramowania. Aby pobrać dodatek na liście, zobacz [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Debugować instalacji lub ładowania problemów za pomocą procesu monitora
Jeśli dodatek ma problemy ze zgodnością podczas instalacji lub obciążenia, może być związana z problemów z dostępem do plików i rejestru. Użyj [Monitor procesu](/sysinternals/downloads/procmon) lub podobnego narzędzia debugowania do logowania się i porównaj zachowanie przeciwko środowisku pracy, aby ułatwić zidentyfikowanie problemu.
