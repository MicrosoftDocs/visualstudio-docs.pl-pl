---
title: Konfigurowanie sesji wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bdf1c372ffcb3ad3a0ebf102827565853947e2b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777871"
---
# <a name="configure-performance-sessions"></a>Konfigurowanie sesji wydajności
Korzystając z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania, można zbierać szeroką gamę danych o wydajności dla dużej liczby typów aplikacji. W tej sekcji przedstawiono sposób użycia właściwości Wizardand wydajności sesji wydajności i docelowego pliku binarnego w celu skonfigurowania narzędzia profilowania w celu zebrania interesujących Cię danych. Właściwości konfiguracji narzędzia profilowania mogą być również używane do kontrolowania ilości danych zbieranych w ramach uruchomienia profilowania. Aby uzyskać więcej informacji, zobacz [Kontrola zbierania danych](../profiling/controlling-data-collection.md).

> [!NOTE]
> W wielu przypadkach korzystanie z właściwości domyślnych Kreatora wydajności jest efektywnym sposobem na zbieranie danych profilowania. Aby uzyskać więcej informacji, zobacz temat [Przewodnik początkujący dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md) i rozpoczynanie [pracy](../profiling/getting-started-with-performance-tools.md).

## <a name="common-tasks"></a>Wspólne zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Ustaw podstawowe opcje profilowania:** Należy skonfigurować [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] do korzystania z serwera symboli firmy Microsoft. Dzięki temu masz dostęp do symboli, takich jak nazwy funkcji i parametrów, dla bieżącej wersji systemu Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne przed rozpoczęciem sesji profilowania, takie jak uprawnienia systemowe do narzędzi profilowania i nazwy plików danych profilowania. | -   [instrukcje: odwołania do informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [jak: serializować informacje o symbolach](../profiling/how-to-serialize-symbol-information.md)<br />-   [: Ustawianie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Określ dane, które mają być zbierane:** Procedury służące do konfigurowania sesji profilowania zależą od typu aplikacji docelowej, która ma być profilowania, oraz typu danych wydajności, które mają być zbierane. | -   [jak: wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)<br />-   [zbierać dane statystyczne wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieraj dane alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [zbierać dane współbieżności wątków i procesów](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [zbieranie dodatkowych danych dotyczących wydajności](../profiling/collecting-additional-performance-data.md) |
| **Ustaw zaawansowane opcje konfiguracji:** Podczas profilowania .NET Framework aplikacji ładujących wiele wersji środowiska uruchomieniowego języka wspólnego (CLR) można określić, która wersja ma być przeprofilowania. Jeśli masz wiele plików exe w sesji wydajności, możesz ustawić kolejność uruchamiania plików binarnych. | -   [: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [jak określić plik binarny do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Sekcje pokrewne
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Zobacz także
- [Eksplorator wydajności](../profiling/performance-explorer.md)
