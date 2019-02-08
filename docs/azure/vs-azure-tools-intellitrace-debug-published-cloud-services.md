---
title: Debugowanie opublikowanej usługi za pomocą IntelliTrace w chmurze platformy Azure
description: Dowiedz się, jak debugowanie usługi w chmurze za pomocą programu Visual Studio i funkcji IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: 3882f52dc38364b0ff325c49964fa907ee8a26ce
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927948"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace
Po uruchomieniu na platformie Azure przy użyciu funkcji IntelliTrace, możesz rejestrować wyczerpujące informacje debugowania dla wystąpienia roli. Jeśli potrzebujesz znaleźć przyczynę problemu, można użyć dzienników IntelliTrace do kroku przez kod z programu Visual Studio, tak jakby były uruchamiane na platformie Azure. W efekcie funkcja IntelliTrace ma rejestrować klucza wykonywania kodu i środowisko danych aplikacji platformy Azure działa jako usługa w chmurze na platformie Azure, gdy pozwala odtwarzać zapisane dane z programu Visual Studio.

Można użyć funkcji IntelliTrace, jeśli masz program Visual Studio Enterprise i usługi Azure application obiektów docelowych programu .NET Framework 4 lub nowszej. IntelliTrace zbiera informacje dotyczące poszczególnych ról platformy Azure. Maszyny wirtualne dla tych ról są zawsze uruchamiane w 64-bitowych systemach operacyjnych.

Alternatywnie, można użyć [zdalne debugowanie](http://go.microsoft.com/fwlink/p/?LinkId=623041) można dołączyć bezpośrednio do usługi w chmurze, która działa na platformie Azure.

> [!IMPORTANT]
> Funkcja IntelliTrace jest przeznaczona dla scenariuszy debugowania tylko, a nie powinny być używane w przypadku wdrożenia produkcyjnego.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurowanie aplikacji platformy Azure dla funkcji IntelliTrace
Aby włączyć funkcji IntelliTrace dla aplikacji platformy Azure, musi tworzenie i publikowanie aplikacji z projektu programu Visual Studio na platformie Azure. Należy skonfigurować IntelliTrace dla aplikacji systemu Azure, przed opublikowaniem jej na platformie Azure. Jeśli publikujesz aplikację bez konieczności konfigurowania funkcji IntelliTrace, musisz ponownie opublikować projekt. Aby uzyskać więcej informacji, zobacz [publikowania usługi Azure cloud services projektów przy użyciu programu Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Gdy wszystko jest gotowe do wdrożenia aplikacji platformy Azure, sprawdź, czy projekt jest ukierunkowany kompilacji są ustawione na **debugowania**.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **Publikuj**.

1. W **publikowanie aplikacji platformy Azure** okno dialogowe, wybierz subskrypcję platformy Azure i wybierz **dalej**.

1. W **ustawienia** wybierz opcję **Zaawansowane ustawienia** kartę.

1. Włącz **Włącz IntelliTrace** opcję, aby zbierać dzienniki IntelliTrace dla aplikacji, gdy zostanie opublikowany w chmurze.

1. Aby dostosować podstawową konfigurację funkcji IntelliTrace, wybierz opcję **ustawienia** obok **Włącz IntelliTrace**.

    ![Link ustawienia funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. W **ustawienia narzędzia IntelliTrace** okna dialogowego, można określić zdarzeń do dziennika, czy należy zebrać informacje wywołań, które moduły i procesy, aby zbierać dzienniki i ilości wykorzystanego miejsca można przydzielić do rejestrowania. Aby uzyskać więcej informacji na temat IntelliTrace, zobacz [debugowania za pomocą IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).

    ![Ustawienia funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Dziennik funkcji IntelliTrace jest cyklicznego pliku dziennika maksymalnego rozmiaru określonego w ustawieniach funkcji IntelliTrace (domyślny rozmiar to 250 MB). Dzienniki funkcji IntelliTrace są zbierane do pliku w systemie plików maszyny wirtualnej. W przypadku żądania dzienniki, migawki jest wykonywane w danym momencie i pobrany na komputer lokalny.

Po opublikowaniu usługi w chmurze platformy Azure do platformy Azure można określić, jeśli IntelliTrace zostało włączone w węźle platformy Azure w **Eksploratora serwera**, jak pokazano na poniższej ilustracji:

![Server Explorer — funkcja IntelliTrace jest włączony](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Pobierz dzienniki IntelliTrace dla wystąpienia roli
W programie Visual Studio można pobrać dzienników IntelliTrace dla wystąpienia roli wykonaj następujące czynności:

1. W **Eksploratora serwera**, rozwiń węzeł **usług w chmurze** węzeł i Znajdź wystąpienie roli dzienników, którego chcesz pobrać.

1. Kliknij prawym przyciskiem myszy wystąpienie roli, a następnie wybierz z menu kontekstowego s **wyświetlanie dzienników IntelliTrace**.

    ![Wyświetlanie opcji menu Dzienniki funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Dzienniki IntelliTrace są pobierane do pliku w katalogu na komputerze lokalnym. Rejestruje każdorazowo zażądania IntelliTrace, jest tworzona nowa migawka. Podczas pobierania dzienników programu Visual Studio Wyświetla postęp operacji w **dziennika aktywności platformy Azure** okna. Jak pokazano na poniższej ilustracji, można rozwinąć element wiersza dla operacji wyświetlić więcej szczegółów.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Możesz kontynuować pracę w programie Visual Studio, podczas pobierania dzienników IntelliTrace. Dziennik zakończył pobieranie, zostanie otwarty w programie Visual Studio.

> [!NOTE]
> Dzienniki IntelliTrace może zawierać wyjątki, które generuje platformę i obsługuje go później. Wewnętrzną strukturę kod generuje te wyjątki, jako część normalnego uruchamiania roli, dzięki czemu można je bezpiecznie zignorować.
>
>

## <a name="next-steps"></a>Następne kroki
- [Opcje debugowania usług Azure cloud services](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikowanie usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)