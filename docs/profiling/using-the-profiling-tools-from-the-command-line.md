---
title: Korzystanie z narzędzi profilowania z wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1420aa9f92e8ef7564478499c78393510ad61c23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778040"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Korzystanie z narzędzi profilowania z wiersza polecenia
Narzędzia wiersza polecenia narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania można używać do profilowania aplikacji w wierszu polecenia i do automatyzacji profilowania przy użyciu plików wsadowych i skryptów. Można również wygenerować pliki raportu w wierszu polecenia. Za pomocą lekkiego profilera autonomicznego można zbierać dane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na komputerach, które nie zostały zainstalowane.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Ustaw położenie symboli:** Aby wyświetlić nazwy funkcji i parametrów, profiler musi mieć dostęp do symbolu (.* pdb)* plików profilowanych plików binarnych. Pliki te powinny zawierać pliki symboli systemu operacyjnego firmy Microsoft i aplikacje, które mają być wyświetlane w analizie. Za pomocą publicznego serwera symboli firmy Microsoft można upewnić się, że masz poprawny plik . *plików pdb* dla plików binarnych firmy Microsoft. | -   [Jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profiluj swoją aplikację:** Narzędzia wiersza polecenia i opcje używane do profilowania aplikacji docelowej zależą od typu aplikacji, metody profilowania i tego, czy obiekt docelowy jest aplikacją zarządzaną, czy natywną. | -   [Używanie metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md) |
| **Tworzenie raportów xml i csv:** Profilowanie w wierszu polecenia tworzy pliki danych, które [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]można przeglądać w interfejsie dla . Można również wygenerować . *xml* lub wartość oddzielona przecinkami (.* csv)* przy użyciu narzędzia wiersza polecenia VSPerfReport. | -   [Tworzenie raportów profilera z wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [Vsperfreport](../profiling/vsperfreport.md) |
| **Kod profilu na komputerach bez programu Visual Studio:** Autonomicznego profilra narzędzia profilowania można używać do zbierania danych dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aplikacji na komputerach, które nie zostały zainstalowane. | -   [Jak: Zainstaluj samodzielny profiler](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Dokumentacja
- [Odwołanie do narzędzi profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
