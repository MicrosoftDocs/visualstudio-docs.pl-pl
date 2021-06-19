---
title: Ustawienia projektu dla konfiguracji debugowania w języku C# | Microsoft Docs
description: Dowiedz się, jak zmienić ustawienia projektu dla konfiguracji debugowania języka C# w programie Visual Studio, korzystając z karty Debugowanie i karty Kompilacja na stronach właściwości projektu.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3377187412f95e090c7403ddd6f898a18f6cec9f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386504"
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w języku C#

Ustawienia debugowania projektu w języku C# można zmienić na karcie [Debugowanie](#debug-tab) i [na karcie Kompilacja](#build-tab) na stronach właściwości projektu.

Aby otworzyć strony właściwości, wybierz projekt w oknie  **Eksplorator rozwiązań** a następnie wybierz ikonę Właściwości lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

Aby uzyskać więcej informacji, zobacz [Debug and release configurations (Konfiguracje debugowania i wydania).](how-to-set-debug-and-release-configurations.md)

>[!IMPORTANT]
>Te ustawienia nie mają zastosowania do aplikacji platformy .NET Core, ASP.NET ani aplikacji platformy uniwersalnej systemu Windows. Aby skonfigurować ustawienia debugowania dla aplikacji platformy uniwersalnej systemu Windows, zobacz [Rozpoczynanie sesji debugowania dla aplikacji platformy uniwersalnej systemu Windows.](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="debug-tab"></a>Karta Debugowanie

|Ustawienie|Opis|
|-------------------------------------| - |
| **Konfiguracja** | Ustawia tryb tworzenia aplikacji. Z listy rozwijanej wybierz pozycję  Aktywne **(debugowanie),** **Debuguj,** Wydanie lub Wszystkie konfiguracje.  |
| **Akcja uruchamiania** | Określa akcję po wybraniu **przycisku Rozpocznij** w konfiguracji debugowania.<br />- **Domyślnym** ustawieniem jest projekt startowy, który uruchamia projekt startowy na potrzeby debugowania. Aby uzyskać więcej informacji, zobacz [Wybieranie projektu startowego](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Uruchamianie programu zewnętrznego** rozpoczyna się i dołącza do aplikacji, która nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [Dołączanie do uruchomionych procesów za pomocą debugera](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Przeglądarka Start z adresem URL** umożliwia debugowanie aplikacji internetowej. |
| **Opcje uruchamiania**  >  **Argumenty wiersza polecenia** | Określa argumenty wiersza polecenia dla debugowanych aplikacji. Nazwa polecenia to nazwa aplikacji określona w **poleceniu Uruchom program zewnętrzny.** |
| **Opcje uruchamiania**  >  **Katalog roboczy** | Określa katalog roboczy debugowanych aplikacji. W języku C# katalog roboczy to *domyślnie \bin\debug.*
| **Opcje uruchamiania**  >  **Korzystanie z maszyny zdalnej**|W przypadku debugowania zdalnego wybierz tę opcję i wprowadź nazwę docelowego debugowania zdalnego lub nazwę serwera [Msvsmon.](../debugger/remote-debugging.md) <br />Lokalizacja aplikacji na maszynie zdalnej jest określana przez właściwość **Ścieżka danych** wyjściowych na **karcie Kompilacja.** Lokalizacja musi być katalogiem współużytowalnym na maszynie zdalnej.
| **Aparat debugera**  >  **Włączanie niezamanagenego debugowania kodu** | Debuguje wywołania do natywnego (nieza zarządzania) kodu Win32 z aplikacji zarządzanej. |
| **Aparat debugera**  >  **Włączanie SQL Server debugowania** | Debuguje SQL Server bazy danych. |

## <a name="build-tab"></a>Karta Kompilacja

|Ustawienie|Opis|
|-------------|-----------------|
|**Ogólne**  >  **Symbole kompilacji warunkowej**|Zdefiniuj stałe DEBUG i TRACE, jeśli są zaznaczone.<br /><br /> Te stałe umożliwiają warunkową kompilację [klasy Debug i](/dotnet/api/system.diagnostics.debug) klasy [Trace](/dotnet/api/system.diagnostics.trace). Po zdefiniowanych stałych metody klasy Debug i Trace generują dane wyjściowe w [oknie Dane wyjściowe](../ide/reference/output-window.md). Bez tych stałych metody klasy Debug i Trace nie są kompilowane i nie są generowane żadne dane wyjściowe.<br /><br />Zazwyczaj debugowanie jest definiowane w wersji debugowania kompilacji i niezdefiniowane w wersji wydania. Trace jest zdefiniowany zarówno w wersji debugowania, jak i wersji wydania.|
|**Ogólne**  >  **Optymalizowanie kodu**|Jeśli usterka nie pojawia się tylko w zoptymalizowanym kodzie, pozostaw to ustawienie bez opcji Debuguj kompilacje. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ instrukcje nie odpowiadają bezpośrednio instrukcjiom w kodzie źródłowym.|
|**Dane wyjściowe**  >  **Ścieżka wyjściowa**|Zazwyczaj ustawiono wartość *bin\Debug na* potrzeby debugowania.|
|**Przycisk** Zaawansowane|Aby uzyskać informacje na temat zaawansowanych opcji debugowania, zobacz okno dialogowe [Zaawansowane ustawienia kompilacji (C#).](../ide/reference/advanced-build-settings-dialog-box-csharp.md) Przenośny format plików symboli *(.pdb)* to najnowszy format międzyplatformowy dla aplikacji platformy .NET Core.

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)