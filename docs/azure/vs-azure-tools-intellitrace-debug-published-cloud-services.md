---
title: Debuguj opublikowaną usługę w chmurze platformy Azure za pomocą usługi IntelliTrace
ms.custom: SEO-VS-2020
description: Dowiedz się, jak debugować usługę w chmurze za pomocą programu Visual Studio i IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: b89ed536e6483f54d4d7370a02935728dedfb517
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809823"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace
Za pomocą IntelliTrace można rejestrować obszerne informacje o debugowaniu dla wystąpienia roli uruchomionego na platformie Azure. Jeśli chcesz znaleźć przyczynę problemu, możesz użyć dzienników IntelliTrace, aby przejść do kodu z programu Visual Studio, tak jakby był uruchomiony na platformie Azure. W efekcie IntelliTrace rejestruje kod klucza i dane środowiska, gdy aplikacja platformy Azure działa jako usługa w chmurze na platformie Azure i umożliwia odtwarzanie zarejestrowanych danych z programu Visual Studio.

Możesz użyć IntelliTrace, jeśli masz zainstalowaną Visual Studio Enterprise i Twoje aplikacje platformy Azure mają .NET Framework 4 lub nowszą wersję. IntelliTrace zbiera informacje dla ról platformy Azure. Maszyny wirtualne dla tych ról są zawsze uruchamiane 64-bitowe systemy operacyjne.

Alternatywnie możesz użyć [zdalnego debugowania](vs-azure-tools-debugging-cloud-services-overview.md) , aby dołączyć bezpośrednio do usługi w chmurze działającej na platformie Azure.

> [!IMPORTANT]
> IntelliTrace jest przeznaczona tylko do scenariuszy debugowania i nie należy go używać do wdrożenia produkcyjnego.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurowanie aplikacji platformy Azure dla usługi IntelliTrace
Aby włączyć IntelliTrace dla aplikacji platformy Azure, musisz utworzyć i opublikować aplikację z projektu programu Visual Studio platformy Azure. Musisz skonfigurować IntelliTrace dla swojej aplikacji platformy Azure przed opublikowaniem jej na platformie Azure. W przypadku publikowania aplikacji bez konfigurowania IntelliTrace należy ponownie opublikować projekt. Aby uzyskać więcej informacji, zobacz [Publikowanie projektów usług Azure Cloud Services przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

1. Gdy wszystko będzie gotowe do wdrożenia aplikacji platformy Azure, sprawdź, czy obiekty docelowe kompilacji projektu są ustawione na **debugowanie**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję projekt, a następnie z menu kontekstowego wybierz pozycję **Publikuj**.

1. W oknie dialogowym **publikowanie aplikacji platformy** Azure wybierz subskrypcję platformy Azure, a **następnie**wybierz pozycję Dalej.

1. Na stronie **Ustawienia** wybierz kartę **Ustawienia zaawansowane** .

1. Włącz opcję **Włącz IntelliTrace** , aby zbierać dzienniki IntelliTrace dla aplikacji po opublikowaniu jej w chmurze.

1. Aby dostosować podstawową konfigurację IntelliTrace, wybierz pozycję **Ustawienia** obok pozycji **Włącz IntelliTrace**.

    ![Link ustawień IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. W oknie dialogowym **Ustawienia IntelliTrace** można określić, które zdarzenia mają być rejestrowane, w jaki sposób zbierać informacje o wywołaniach, moduły i procesy do zbierania dzienników oraz ilość miejsca przydzielonego do nagrania. Aby uzyskać więcej informacji na temat IntelliTrace, zobacz [debugowanie z IntelliTrace](../debugger/intellitrace.md).

    ![Ustawienia IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Dziennik IntelliTrace jest cyklicznym plikiem dziennika o maksymalnym rozmiarze określonym w ustawieniach IntelliTrace (rozmiar domyślny to 250 MB). Dzienniki IntelliTrace są zbierane do pliku w systemie plików maszyny wirtualnej. Po zażądaniu dzienników migawka jest wykonywana w tym momencie i pobierana na komputer lokalny.

Po opublikowaniu usługi w chmurze platformy Azure na platformie Azure Możesz określić, czy IntelliTrace został włączony z poziomu węzła platformy Azure w **Eksplorator serwera**, jak pokazano na poniższej ilustracji:

![Eksplorator serwera — IntelliTrace włączony](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Pobieranie dzienników IntelliTrace dla wystąpienia roli
Za pomocą programu Visual Studio można pobrać dzienniki IntelliTrace dla wystąpienia roli, wykonując następujące czynności:

1. W **Eksplorator serwera**rozwiń węzeł **Cloud Services** i zlokalizuj wystąpienie roli, którego dzienniki chcesz pobrać.

1. Kliknij prawym przyciskiem myszy wystąpienie roli, a następnie z menu kontekstowego s wybierz opcję **Wyświetl dzienniki IntelliTrace**.

    ![Opcja menu wyświetlania dzienników IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Dzienniki IntelliTrace są pobierane do pliku w katalogu na komputerze lokalnym. Za każdym razem, gdy zażądano dzienników IntelliTrace, tworzona jest Nowa migawka. Podczas pobierania dzienników program Visual Studio wyświetla postęp operacji w oknie **Dziennik aktywności platformy Azure** . Jak pokazano na poniższej ilustracji, można rozwinąć element linii dla operacji, aby zobaczyć więcej szczegółów.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Podczas pobierania dzienników IntelliTrace można nadal korzystać z programu Visual Studio. Po zakończeniu pobierania dziennika zostanie on otwarty w programie Visual Studio.

> [!NOTE]
> Dzienniki IntelliTrace mogą zawierać wyjątki, które platforma generuje i obsługuje później. Wewnętrzny kod struktury generuje te wyjątki jako normalną część uruchamiania roli, dzięki czemu można je bezpiecznie zignorować.
>
>

## <a name="next-steps"></a>Następne kroki
- [Opcje debugowania usług Azure Cloud Services](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikowanie usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)