---
title: Za pomocą profilowania narzędzia z wiersza polecenia | Dokumentacja firmy Microsoft
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
ms.workload:
- multiple
ms.openlocfilehash: 936d2bfe4eecd3e36553cef7c5779f201e190619
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615822"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Użyj narzędzi profilowania z wiersza polecenia
Można użyć narzędzia wiersza poleceń dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools do profilu aplikacji w wierszu polecenia i zautomatyzować profilowania przy użyciu plików wsadowych i skryptów. Można również wygenerować pliki raportu w wierszu polecenia. Uproszczone autonomicznego profilera można użyć do zbierania danych na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Wspólne zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Ustaw lokalizację symboli:** Aby wyświetlić nazwy funkcji i parametrów, program profilujący musi mieć dostęp do symbolu (. *plik PDB*) plików profilowanych danych binarnych. Pliki te powinny obejmować pliki symboli dla Microsoft systemu operacyjnego i aplikacji, które mają być wyświetlane w analizy. Można użyć serwera publicznego symboli firmy Microsoft, aby upewnić się, że masz właściwą. *pdb* plików dla danych binarnych firmy Microsoft. | -   [Jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profiluj aplikację:** Narzędzia wiersza polecenia i opcje używane do profilu aplikacji docelowej są zależne od typu aplikacji, metody profilowania i tego, czy element docelowy jest aplikacją zarządzane lub natywne. | -   [Korzystanie z metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md) |
| **Tworzenie raportów XML i CSV:** Profilowanie w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można również wygenerować. *xml* lub wartości rozdzielanych przecinkami (. *CSV*) pliki danych przy użyciu narzędzia wiersza polecenia VSPerfReport. | -   [Tworzenie raportów profilera z wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Kod profilu na komputerach bez programu Visual Studio:** Autonomiczny profilera Profiling Tools umożliwiają zbieranie danych dla aplikacji na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane. | -   [Jak: Instalowanie autonomicznego profilera](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Tematy pomocy
- [Informacje dotyczące wiersza polecenia Profiling Tools](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Zobacz także
- [Eksplorator wydajności](../profiling/performance-explorer.md)