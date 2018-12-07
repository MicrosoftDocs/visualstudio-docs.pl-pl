---
title: Ustawienia dla projektu C# debugowania konfiguracji | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6de7bfd547516b227063c0d3143b508bcbd9ddfd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059275"
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w języku C#

Możesz zmienić C# ustawienia debugowania w programie project [karty debugowania](#debug-tab) i [karta kompilacji](#build-tab) stron właściwości projektu. 

Aby otworzyć na stronach właściwości, wybierz projekt w **Eksploratora rozwiązań** , a następnie wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**.

Aby uzyskać więcej informacji, zobacz [debugowania i zwalniania konfiguracji](how-to-set-debug-and-release-configurations.md). 

>[!IMPORTANT]
>Te ustawienia nie dotyczą aplikacji .NET Core, ASP.NET lub platformy uniwersalnej systemu Windows. Aby skonfigurować ustawienia debugowania dla aplikacji platformy uniwersalnej systemu Windows, zobacz [uruchamianie sesji debugowania dla aplikacji platformy uniwersalnej systemu Windows](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a>Debugowanie kartę  
  
|Ustawienie|Opis|
|-------------------------------------| - |
| **Konfiguracja** | Ustawia tryb w celu skompilowania aplikacji. Wybierz **aktywna (debugowanie)**, **debugowania**, **wersji**, lub **wszystkie konfiguracje** z listy rozwijanej. |
| **Akcja uruchamiania** | Określa akcję po wybraniu **Start** w konfiguracji debugowania.<br />- **Rozpocznij projekt** jest ustawieniem domyślnym i uruchamia projekt startowy do debugowania. Aby uzyskać więcej informacji, zobacz [Wybieranie projektu startowego](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Uruchom zewnętrzny program** rozpoczyna się i dołącza do aplikacji, która nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionego procesu za pomocą debugera](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Uruchom przeglądarkę z adresem URL** umożliwia debugowanie aplikacji sieci web. |
| **Opcje uruchamiania** > **argumenty wiersza polecenia** | Określa argumenty wiersza polecenia aplikacji debugowane. Nazwa polecenia jest nazwa aplikacji, określona w **uruchomienia programu zewnętrznego**. |
| **Opcje uruchamiania** > **katalog roboczy** | Określa katalog roboczy aplikacji debugowane. W C#, katalog roboczy jest *\bin\debug* domyślnie.
| **Opcje uruchamiania** > **maszyny zdalnej użycia**|Dla zdalnego debugowania, wybierz tę opcję, a następnie wprowadź nazwę docelowy debugowania zdalnego lub [nazwy serwera Msvsmon](../debugger/remote-debugging.md). <br />Lokalizacja aplikacji na komputerze zdalnym jest określona przez **ścieżkę wyjściową** właściwość **kompilacji** kartę. Lokalizacja musi być możliwe do udostępnienia katalogu na komputerze zdalnym. 
| **Aparat debugera** > **włączenia debugowania niezarządzanego kodu** | Debuguje wywołań do kodu natywnego (niezarządzanego) Win32 z zarządzanych aplikacji. |
| **Aparat debugera** > **programu SQL Server Włącz debugowanie** | Debuguje obiekty bazy danych programu SQL Server. |
  
## <a name="build-tab"></a>Tworzenie karty  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Ogólne** > **symbole kompilacji warunkowej**|Definiuj stałe debugowania i śledzenia, jeśli wybrana.<br /><br /> Te stałe Włącz kompilację warunkową [Klasa Debug](/dotnet/api/system.diagnostics.debug) i [klasa śledzenia](/dotnet/api/system.diagnostics.trace). Za pomocą tych zdefiniowanych stałych, debugowania i śledzenia metod klasy generują dane wyjściowe do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tych stałe debugowania i śledzenia metod klasy nie są kompilowane i generowane żadne dane wyjściowe.<br /><br />Zazwyczaj debugowania jest zdefiniowany w wersji do debugowania kompilacji i niezdefiniowana w pełnej wersji. TRACE jest zdefiniowane w wersji debugowania i wydania.|  
|**Ogólne** > **Optymalizuj kod**|Jeśli błąd pojawia się tylko w zoptymalizowanym kodzie, należy pozostawić to ustawienie, niezaznaczone w przypadku kompilacji debugowania. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ instrukcje nie odpowiadają bezpośrednio do instrukcji w kodzie źródłowym.|  
|**Dane wyjściowe** > **ścieżka wyjściowa**|Zazwyczaj równa *bin\Debug* do debugowania.|
|**Zaawansowane** przycisku|Aby uzyskać informacje na temat zaawansowanych opcji debugowania, zobacz [okno dialogowe Ustawienia zaawansowane kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Przenośne formatu dla symbolu (*.pdb*) plików to ostatnie format Międzyplatformowe aplikacje platformy .NET Core. 
  
## <a name="see-also"></a>Zobacz także  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)