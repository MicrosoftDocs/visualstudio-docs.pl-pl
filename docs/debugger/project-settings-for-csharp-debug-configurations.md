---
title: Ustawienia projektu dla konfiguracji debugowania w języku C# | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904065"
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w języku C#

Ustawienia debugowania projektu C# można zmienić na [karcie debugowanie](#debug-tab) i na [karcie kompilacja](#build-tab) na stronach właściwości projektu.

Aby otworzyć strony właściwości, wybierz projekt w **Eksplorator rozwiązań** a następnie wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

Aby uzyskać więcej informacji, zobacz [debugowanie i wydawanie konfiguracji](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Te ustawienia nie dotyczą aplikacji .NET Core, ASP.NET lub platformy UWP. Aby skonfigurować ustawienia debugowania dla aplikacji platformy UWP, zobacz [Rozpoczynanie sesji debugowania dla aplikacji platformy UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Karta debugowanie

|Ustawienie|Opis|
|-------------------------------------| - |
| **Konfiguracja** | Ustawia tryb tworzenia aplikacji. Wybierz pozycję **aktywne (Debuguj)**, **Debuguj**, **wydawanie**lub **wszystkie konfiguracje** z listy rozwijanej. |
| **Uruchom akcję** | Określa akcję w przypadku wybrania opcji **Rozpocznij** w konfiguracji debugowania.<br />- **Początkowy projekt** jest domyślnie i uruchamia projekt startowy na potrzeby debugowania. Aby uzyskać więcej informacji, zobacz [Wybierz projekt startowy](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Uruchom program zewnętrzny** i dołącza do aplikacji, która nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów z debugerem](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Polecenie Uruchom przeglądarkę z adresem URL** umożliwia debugowanie aplikacji sieci Web. |
| **Opcje uruchamiania**  >  **Argumenty wiersza polecenia** | Określa argumenty wiersza polecenia dla debugowanej aplikacji. Nazwa polecenia to nazwa aplikacji określona w **początkowym programie zewnętrznym**. |
| **Opcje uruchamiania**  >  **Katalog roboczy** | Określa katalog roboczy debugowanej aplikacji. W języku C# katalog roboczy jest domyślnie *\bin\debug* .
| **Opcje uruchamiania**  >  **Użyj maszyny zdalnej**|Na potrzeby debugowania zdalnego wybierz tę opcję, a następnie wprowadź nazwę docelowego zdalnego debugowania lub [nazwę serwera msvsmon](../debugger/remote-debugging.md). <br />Lokalizacja aplikacji na maszynie zdalnej jest określona przez właściwość **Ścieżka wyjściowa** na karcie **kompilacja** . Lokalizacja musi być katalogiem udostępnionym na komputerze zdalnym.
| **Aparat debugera**  >  **Włącz debugowanie kodu niezarządzanego** | Debuguje wywołania natywnego (niezarządzanego) kodu Win32 z zarządzanej aplikacji. |
| **Aparat debugera**  >  **Włącz debugowanie SQL Server** | Debuguje SQL Server obiekty bazy danych. |

## <a name="build-tab"></a>Karta kompilacja

|Ustawienie|Opis|
|-------------|-----------------|
|**Ogólne**  >  **Symbole kompilacji warunkowej**|Zdefiniuj stałe debugowania i śledzenia, jeśli są zaznaczone.<br /><br /> Te stałe umożliwiają kompilację warunkową [klasy debugowania](/dotnet/api/system.diagnostics.debug) i [klasy śledzenia](/dotnet/api/system.diagnostics.trace). Dzięki tym stałym definicjom metody klasy Debug i Trace generują dane wyjściowe do [okna danych wyjściowych](../ide/reference/output-window.md). Bez tych stałych metody klasy Debug i Trace nie są kompilowane i nie są generowane żadne dane wyjściowe.<br /><br />Zwykle debugowanie jest zdefiniowane w wersji debugowania kompilacji i niezdefiniowane w wersji. ŚLEDZENIE jest zdefiniowane w wersji Debug i Release.|
|**Ogólne**  >  **Optymalizuj kod**|Jeśli usterka nie występuje tylko w zoptymalizowanym kodzie, pozostaw to ustawienie niezaznaczone dla kompilacji debugowania. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ instrukcje nie odpowiadają bezpośrednio na instrukcje w kodzie źródłowym.|
|**Dane wyjściowe**  >  **Ścieżka wyjściowa**|Zwykle ustawiona na *bin\Debug* na potrzeby debugowania.|
|Przycisk **Zaawansowane**|Aby uzyskać informacje na temat zaawansowanych opcji debugowania, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Przenośny format plików symboli (*. pdb*) jest ostatnim formatem dla aplikacji platformy .NET Core.

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)