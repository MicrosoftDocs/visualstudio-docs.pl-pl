---
title: Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą funkcji IntelliTrace
description: Dowiedz się, jak debugować usługę w chmurze za pomocą programów Visual Studio i IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: c61af4a08c61cbfd16d33e2b5cf7402960163f12
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489717"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace
Za pomocą intellitrace można rejestrować szczegółowe informacje debugowania dla wystąpienia roli, gdy jest uruchamiany na platformie Azure. Jeśli chcesz znaleźć przyczynę problemu, można użyć dzienników IntelliTrace, aby przejść przez kod z programu Visual Studio, tak jakby był uruchomiony na platformie Azure. W efekcie IntelliTrace rejestruje wykonanie kodu klucza i dane środowiska, gdy aplikacja platformy Azure jest uruchomiona jako usługa w chmurze na platformie Azure i umożliwia odtworzenia zarejestrowanych danych z programu Visual Studio.

Funkcji IntelliTrace można użyć, jeśli masz zainstalowany program Visual Studio Enterprise i obiekty docelowe aplikacji platformy Azure .NET Framework 4 lub nowszej. IntelliTrace zbiera informacje dotyczące ról platformy Azure. Maszyny wirtualne dla tych ról zawsze działają 64-bitowe systemy operacyjne.

Alternatywnie można użyć [zdalnego debugowania,](vs-azure-tools-debugging-cloud-services-overview.md) aby dołączyć bezpośrednio do usługi w chmurze, która jest uruchomiona na platformie Azure.

> [!IMPORTANT]
> IntelliTrace jest przeznaczony tylko do scenariuszy debugowania i nie powinny być używane do wdrożenia produkcyjnego.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurowanie aplikacji platformy Azure dla funkcji IntelliTrace
Aby włączyć IntelliTrace dla aplikacji platformy Azure, należy utworzyć i opublikować aplikację z projektu platformy Visual Studio Azure. Przed opublikowaniem jej na platformie Azure należy skonfigurować narzędzie IntelliTrace dla aplikacji platformy Azure. Jeśli publikujesz aplikację bez konfigurowania IntelliTrace, należy ponownie opublikować projekt. Aby uzyskać więcej informacji, zobacz [Publikowanie projektów usług w chmurze platformy Azure przy użyciu programu Visual Studio.](vs-azure-tools-publishing-a-cloud-service.md)

1. Gdy będziesz gotowy do wdrożenia aplikacji platformy Azure, sprawdź, czy obiekty docelowe kompilacji projektu są ustawione na **Debugowanie.**

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Publikuj**.

1. W oknie dialogowym **Publikowanie aplikacji platformy Azure** wybierz subskrypcję platformy Azure i wybierz pozycję **Dalej**.

1. Na stronie **Ustawienia** wybierz kartę **Ustawienia zaawansowane.**

1. Włącz włącz opcję **Włącz intellitrace,** aby zbierać dzienniki IntelliTrace dla aplikacji, gdy jest publikowana w chmurze.

1. Aby dostosować podstawową konfigurację IntelliTrace, wybierz pozycję **Ustawienia** obok pozycji **Włącz intellitrace**.

    ![Łącze ustawień intellitrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. W oknie dialogowym **Ustawienia intellitrace** można określić, które zdarzenia mają być rejestrowane, czy zbierać informacje o wywołaniach, moduły i procesy do zbierania dzienników oraz ilość miejsca do przydzielenia do nagrania. Aby uzyskać więcej informacji na temat intellitrace, zobacz [Debugowanie za pomocą funkcji IntelliTrace](../debugger/intellitrace.md).

    ![Ustawienia IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Dziennik IntelliTrace jest okrągłym plikiem dziennika o maksymalnym rozmiarze określonym w ustawieniach IntelliTrace (domyślny rozmiar to 250 MB). Dzienniki IntelliTrace są zbierane do pliku w systemie plików maszyny wirtualnej. Gdy zażądasz dzienników, migawka jest pobierana w tym momencie i pobierana na komputer lokalny.

Po opublikowaniu usługi w chmurze platformy Azure na platformie Azure można określić, czy funkcja IntelliTrace została włączona w węźle platformy Azure w **Eksploratorze serwera**, jak pokazano na poniższej ilustracji:

![Eksplorator serwerów — funkcja IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Pobieranie dzienników IntelliTrace dla wystąpienia roli
Korzystając z programu Visual Studio, można pobrać dzienniki IntelliTrace dla wystąpienia roli, wykonując następujące kroki:

1. W **Eksploratorze serwera**rozwiń węzeł **Usługi w chmurze** i znajdź wystąpienie roli, którego dzienniki chcesz pobrać.

1. Kliknij prawym przyciskiem myszy wystąpienie roli, a następnie z menu kontekstowego s wybierz polecenie **Wyświetl dzienniki IntelliTrace**.

    ![Wyświetl opcję menu Dzienniki IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Dzienniki IntelliTrace są pobierane do pliku w katalogu na komputerze lokalnym. Za każdym razem, gdy żądasz dzienników IntelliTrace, tworzona jest nowa migawka. Podczas pobierania dzienników program Visual Studio wyświetla postęp operacji w oknie **dziennika aktywności platformy Azure.** Jak pokazano na poniższym rysunku, można rozwinąć element zamówienia dla operacji, aby wyświetlić więcej szczegółów.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Można kontynuować pracę w programie Visual Studio podczas pobierania dzienników IntelliTrace. Po zakończeniu pobierania dziennika zostanie on otwarty w programie Visual Studio.

> [!NOTE]
> Dzienniki IntelliTrace może zawierać wyjątki, które struktura generuje i obsługuje później. Wewnętrzny kod struktury generuje te wyjątki jako normalną część uruchamiania roli, więc można bezpiecznie je zignorować.
>
>

## <a name="next-steps"></a>Następne kroki
- [Opcje debugowania usług w chmurze platformy Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikowanie usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)