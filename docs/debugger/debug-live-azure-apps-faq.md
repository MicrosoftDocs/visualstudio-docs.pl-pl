---
title: Często zadawane pytania dotyczące debugowania migawek | Dokumentacja firmy Microsoft
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853313"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Często zadawane pytania dotyczące debugowania migawek w programie Visual Studio

Poniżej przedstawiono listę pytań, które mogą się podczas debugowania na żywo aplikacji platformy Azure przy użyciu rozszerzenia Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Co to jest to koszt wydajności wykonywania migawki?

Po przechwyceniu przez rozszerzenie Snapshot Debugger migawkę aplikacji rozwidlenia procesu aplikacji i wstrzymuje rozwidlone kopiowania. Podczas debugowania migawki debugowania względem rozwidlone kopię procesu. Ten proces zajmuje tylko 10-20 MS, ale nie obejmuje kopiowania pełnego stosu aplikacji. Zamiast tego kopiuje tabeli strony i ustawia strony, aby skopiować przy zapisie. Jeśli niektóre obiekty aplikacji w przypadku zmiany sterty odpowiednich stronach są kopiowane. To serwatki każda migawka zawiera małe w pamięci kosztów (rzędu kilku setki kilobajtów dla większości aplikacji).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co się dzieje w przypadku skalowania w poziomie w usłudze Azure App Service (wiele wystąpień aplikacji)?

Jeśli masz wiele wystąpień aplikacji, punkty przyciągania stosowane do każdego pojedynczego wystąpienia. Tylko pierwszy punkt przyciągania, aby trafić warunkom określonym tworzy migawkę. Jeśli masz wiele punktów przyciągania, nowsze migawek pochodzą z tego samego wystąpienia, jak utworzyć pierwszą migawką. Punkty rejestrowania wysyłany do okna danych wyjściowych będzie wyświetlana tylko komunikaty z jednego wystąpienia, gdy punkty rejestrowania wysyłane do dzienników aplikacji wysyłanie komunikatów z każdego wystąpienia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak rozszerzenie Snapshot Debugger załadować symbole?

Rozszerzenie Snapshot Debugger wymaga posiadania pasujących symboli dla aplikacji lokalnych lub wdrożony do usługi Azure App Service. (Osadzonych plików PDB obecnie nie są obsługiwane.) Rozszerzenie Snapshot Debugger automatycznie pobiera symbole z usługi Azure App Service. Począwszy od programu Visual Studio 2017 wersja 15.2, wdrażanie w usłudze Azure App Service wdraża symbole Twojej aplikacji.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Rozszerzenie Snapshot Debugger działa dla kompilacji wydania mojej aplikacji?

Tak — rozszerzenie Snapshot Debugger jest przeznaczony do pracy dla kompilacji wydania. Gdy punktu przyciągania jest umieszczany w funkcji, funkcja jest ponownie kompilowana do wersji debugowania, dzięki czemu debugowania. Zatrzymywanie rozszerzenia Snapshot Debugger zwraca funkcje do wersji kompilacji wydania.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Punkty rejestrowania może spowodować skutki uboczne w mojej aplikacji produkcyjnych?

Nie — komunikaty dziennika, dodanych do aplikacji są przetwarzane niemal. Nie spowodują one wszelkie efekty uboczne w aplikacji. Jednak niektóre właściwości natywne mogą być niedostępne z punkty rejestrowania.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Rozszerzenie Snapshot Debugger działa Jeśli mój serwer znajduje się pod obciążeniem?

Tak, debugowanie migawki można pracować na serwerach w warunkach obciążenia. Rozszerzenie Snapshot Debugger ogranicza i nie przechwytywania migawek w sytuacjach, gdy istnieje małą ilością wolnej pamięci na serwerze.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Jak odinstalować rozszerzenie Snapshot Debugger?

Możesz odinstalować rozszerzenie witryny Snapshot Debugger w usłudze App Service wykonując następujące kroki:

1. Wyłącz aplikację usługi za pomocą Eksploratora chmury w portalu programu Visual Studio lub na platformie Azure.
1. Przejdź do witryny Kudu usługi App Service (czyli yourappservice. **Menedżer sterowania usługami**. azurewebsites.net) i przejdź do **rozszerzeń witryny**.
1. Kliknij przycisk X w rozszerzenie witryny Snapshot Debugger go usunąć.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Dlaczego porty są otwarte w trakcie sesji rozszerzenia Snapshot Debugger

Rozszerzenie Snapshot Debugger musi otworzyć zestawu portów w celu debugowania migawki wykonane na platformie Azure, są tego samego porty wymagane do zdalnego debugowania. [Listę portów, w tym miejscu można znaleźć](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Debugowanie na żywo aplikacji ASP.NET, przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debugowanie na żywo ASP.NET Azure wirtualnego Machines\Virtual maszyn Scale Sets przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debugowanie na żywo ASP.NET Azure Kubernetes za pomocą rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md)