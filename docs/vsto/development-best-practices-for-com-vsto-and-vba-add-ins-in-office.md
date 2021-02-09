---
title: 'Najlepsze rozwiązania programistyczne: COM, VSTO, & Dodatki VBA w pakiecie Office'
description: Zapoznaj się z zalecanymi najlepszymi rozwiązaniami dotyczącymi tworzenia dodatków COM, VSTO i VBA dla Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d5470c138d4339356ca9f8c79cb5ab274dd99019
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897565"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Najlepsze rozwiązania w zakresie programowania dla dodatków COM, VSTO i VBA w pakiecie Office
  Jeśli tworzysz Dodatki COM, VSTO lub VBA dla pakietu Office, postępuj zgodnie z najlepszymi rozwiązaniami programistycznymi opisanymi w tym artykule.   Dzięki temu:

- Zgodność dodatków w różnych wersjach i wdrożeniach pakietu Office.
- Zmniejszona złożoność wdrożenia dodatku dla użytkowników i administratorów IT.
- Nieoczekiwane instalacje lub błędy środowiska uruchomieniowego dodatku nie występują.

>Uwaga: używanie [mostka programu Desktop](/windows/uwp/porting/desktop-to-uwp-root) do przygotowywania modelu COM, programu VSTO lub dodatku VBA dla Sklepu Windows nie jest obsługiwane. Nie można dystrybuować dodatków COM, VSTO i VBA w Sklepie Windows lub sklepie Office.

## <a name="do-not-check-for-office-during-installation"></a>Nie sprawdzaj pakietu Office podczas instalacji
 Nie zalecamy, aby dodatek wykrył, czy pakiet Office został zainstalowany podczas procesu instalacji dodatku. Jeśli pakiet Office nie jest zainstalowany, można zainstalować dodatek, a użytkownik będzie mógł uzyskać do niego dostęp po zainstalowaniu pakietu Office.

## <a name="use-embedded-interop-types-nopia"></a>Użyj osadzonych typów międzyoperacyjnych (NoPIA)
Jeśli rozwiązanie używa programu .NET 4,0 lub nowszego, użyj osadzonych typów międzyoperacyjnych (NoPIA), a nie w zależności od pakietu redystrybucyjnego podstawowych elementów międzyoperacyjnych (PIA). Użycie osadzania typów zmniejsza rozmiar instalacji rozwiązania i zapewnia przyszłą zgodność. Pakiet Office 2010 to Ostatnia wersja pakietu Office, która dostarczyła pakiet redystrybucyjny PIA. Aby uzyskać więcej informacji, zobacz [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](/previous-versions/ee317478(v=vs.140)) i [równoważność typów i osadzonych typów międzyoperacyjnych](/windows/uwp/porting/desktop-to-uwp-root).

Jeśli Twoje rozwiązanie korzysta ze starszej wersji programu .NET, Zalecamy zaktualizowanie rozwiązania do korzystania z programu .NET 4,0 lub nowszego. Program .NET 4,0 lub nowszy zmniejsza wymagania wstępne środowiska uruchomieniowego w nowszych wersjach systemu Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Unikaj w zależności od konkretnych wersji pakietu Office
Jeśli rozwiązanie używa funkcji, która jest dostępna tylko w nowszych wersjach pakietu Office, sprawdź, czy istnieje możliwość (jeśli jest to możliwe, na poziomie funkcji) w czasie wykonywania (na przykład przy użyciu obsługi wyjątków lub przez sprawdzenie wersji). Sprawdź poprawność wersji minimalnych, a nie określonych wersji, używając obsługiwanych interfejsów API w modelu obiektów, takich jak [Właściwość Application. Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nie zaleca się używania metadanych binarnych pakietu Office, ścieżek instalacji ani kluczy rejestru, ponieważ mogą one ulec zmianie między instalacjami, środowiskami i wersjami.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Włącz zarówno 32-bitowe, jak i 64-bitowe użycie pakietu Office
Domyślna lokalizacja docelowa kompilacji powinna obsługiwać zarówno 32-bitowe (x86), jak i 64-bit (x64), chyba że rozwiązanie zależy od bibliotek, które są dostępne tylko dla określonej liczby bitów. 64-bitowa wersja pakietu Office rośnie, szczególnie w środowiskach danych Big Data. Obsługa zarówno 32-bitowych, jak i 64-bitowych ułatwia użytkownikom przejście między 32-bitowymi i 64-bitowymi wersjami pakietu Office.

Podczas pisania kodu VBA Użyj 64-bitowych bezpiecznych instrukcji DECLARE i Konwertuj zmienne stosownie do potrzeb. Ponadto upewnij się, że dokumenty mogą być udostępniane między użytkownikami z systemami 32-bitowymi lub 64-bitowymi wersjami pakietu Office, dostarczając kod dla każdej liczby bitów. Aby uzyskać więcej informacji, zobacz [64-bitowe Visual Basic for Applications — Omówienie](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Obsługa środowisk z ograniczeniami
Twoje rozwiązanie nie powinno wymagać podniesienia uprawnień konta użytkownika ani uprawnień administratora. Ponadto rozwiązanie nie powinno zależeć od ustawienia lub zmiany:

- Bieżący katalog roboczy
- Katalogi ładowania biblioteki DLL.
- Zmienna PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Zmiana lokalizacji zapisywania danych i ustawień udostępnionych
Jeśli rozwiązanie składa się z dodatku i procesu, który znajduje się poza biurem, nie należy używać folderu Dane aplikacji użytkownika ani rejestru w celu wymiany danych lub ustawień między dodatkiem a procesem zewnętrznym. Zamiast tego należy rozważyć użycie folderu tymczasowego użytkownika, folderu dokumenty lub katalogu instalacyjnego rozwiązania.

## <a name="increment-the-version-number-with-each-update"></a>Zwiększ numer wersji przy każdej aktualizacji
Ustaw numer wersji plików binarnych w rozwiązaniu i zwiększ go wraz z każdą aktualizacją. Ułatwi to użytkownikom identyfikację zmian między wersjami i ocenę zgodności.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Podaj instrukcje pomocy technicznej dla najnowszych wersji pakietu Office
Klienci otrzymują pytania dla niezależnych dostawców oprogramowania, aby zapewnić pomoc techniczną dla dodatków COM, VSTO i VBA, które działają w pakiecie Office. Lista jawnych instrukcji pomocy technicznej ułatwia klientom korzystanie z aplikacji Microsoft 365 w przypadku narzędzi do przygotowywania w przedsiębiorstwie.

Aby zapewnić instrukcje pomocy technicznej dla aplikacji klienckich pakietu Office (na przykład Word lub Excel), należy najpierw sprawdzić, czy dodatki działają w bieżącej wersji pakietu Office, a następnie zatwierdzić w celu udostępnienia aktualizacji, jeśli dodatek zostanie podzielony w przyszłej wersji. Nie ma potrzeby testowania dodatków, gdy firma Microsoft publikuje nową kompilację lub aktualizację pakietu Office. Firma Microsoft rzadko zmienia platformę COM, VSTO i VBA na platformie rozszerzalności w pakiecie Office, a te zmiany będą dobrze udokumentowane.

>Ważne: Firma Microsoft przechowuje listę obsługiwanych dodatków do raportów o gotowości i informacje kontaktowe niezależnego dostawcy oprogramowania. Aby skorzystać z dodatku, zobacz [/ConfigMgr/Desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Użyj Monitora procesów, aby pomóc w debugowaniu instalacji lub ładowania problemów
Jeśli dodatek ma problemy ze zgodnością podczas instalacji lub ładowania, mogą one być związane z problemami z dostępem do plików lub rejestru. Użyj [monitora procesów](/sysinternals/downloads/procmon) lub podobnego narzędzia do debugowania, aby rejestrować i porównywać zachowanie w środowisku roboczym w celu ułatwienia zidentyfikowania problemu.