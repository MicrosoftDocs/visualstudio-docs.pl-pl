---
title: Używanie narzędzia profilowania z wiersza polecenia | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778040"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Używanie narzędzia profilowania z wiersza polecenia
Narzędzia wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania umożliwiają Profilowanie aplikacji w wierszu polecenia i automatyzowanie profilowania przy użyciu plików wsadowych i skryptów. Pliki raportów można również generować w wierszu polecenia. Możesz użyć uproszczonego profilera do zbierania danych na komputerach, na których nie zainstalowano [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Wspólne zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Ustaw lokalizację symboli:** Aby wyświetlić nazwy funkcji i parametrów, profiler musi mieć dostęp do symbolu (. *PDB*) plików plików binarnych, które są profilowane. Pliki te powinny zawierać pliki symboli dla systemu operacyjnego firmy Microsoft i aplikacji, które mają być wyświetlane w analizie. Możesz użyć publicznego serwera symboli firmy Microsoft, aby upewnić się, że masz poprawne. pliki *PDB* dla plików binarnych firmy Microsoft. | -   [: Określanie lokalizacji plików symboli z poziomu wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profiluj aplikację:** Narzędzia wiersza polecenia i opcje używane do profilowania aplikacji docelowej zależą od typu aplikacji, metody profilowania i od tego, czy obiektem docelowym jest aplikacja zarządzana lub natywna. | -   [użyć metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profiluj Aplikacje autonomiczne](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [aplikacji sieci web ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />[usługi profilu](../profiling/command-line-profiling-of-services.md) -    |
| **Tworzenie raportów XML i CSV:** Profilowanie w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Możesz również generować. wartość w *formacie XML* lub przecinkiem (. *pliki CSV*) danych za pomocą narzędzia wiersza polecenia VSPerfReport. | -   [Tworzenie raportów profilera z poziomu wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Kod profilu na komputerach bez programu Visual Studio:** Za pomocą autonomicznego profilera narzędzia profilowania można zbierać dane dla aplikacji na komputerach, na których nie zainstalowano [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [: Instalowanie autonomicznego profilera](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Tematy pomocy
- [Informacje narzędzia profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Zobacz także
- [Eksplorator wydajności](../profiling/performance-explorer.md)
