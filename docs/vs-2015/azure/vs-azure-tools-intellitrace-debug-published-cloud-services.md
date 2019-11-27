---
title: Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i IntelliTrace | Microsoft Docs
description: Dowiedz się, jak debugowanie usługi w chmurze za pomocą programu Visual Studio i funkcji IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 00e13c6f217c54b99dfe103b86f1e775e36fd62a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293537"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace
Po uruchomieniu na platformie Azure przy użyciu funkcji IntelliTrace, możesz rejestrować wyczerpujące informacje debugowania dla wystąpienia roli. Jeśli potrzebujesz znaleźć przyczynę problemu, można użyć dzienników IntelliTrace do kroku przez kod z programu Visual Studio, tak jakby były uruchamiane na platformie Azure. W efekcie funkcja IntelliTrace ma rejestrować klucza wykonywania kodu i środowisko danych aplikacji platformy Azure działa jako usługa w chmurze na platformie Azure, gdy pozwala odtwarzać zapisane dane z programu Visual Studio. 

Można użyć funkcji IntelliTrace, jeśli masz program Visual Studio Enterprise i usługi Azure application obiektów docelowych programu .NET Framework 4 lub nowszej. IntelliTrace zbiera informacje dotyczące poszczególnych ról platformy Azure. Maszyny wirtualne dla tych ról są zawsze uruchamiane w 64-bitowych systemach operacyjnych.

Alternatywnie możesz użyć [zdalnego debugowania](https://go.microsoft.com/fwlink/p/?LinkId=623041) , aby dołączyć bezpośrednio do usługi w chmurze działającej na platformie Azure.

> [!IMPORTANT]
> Funkcja IntelliTrace jest przeznaczona dla scenariuszy debugowania tylko, a nie powinny być używane w przypadku wdrożenia produkcyjnego.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurowanie aplikacji platformy Azure dla funkcji IntelliTrace
Aby włączyć funkcji IntelliTrace dla aplikacji platformy Azure, musi tworzenie i publikowanie aplikacji z projektu programu Visual Studio na platformie Azure. Należy skonfigurować IntelliTrace dla aplikacji systemu Azure, przed opublikowaniem jej na platformie Azure. Jeśli publikujesz aplikację bez konieczności konfigurowania funkcji IntelliTrace, musisz ponownie opublikować projekt. Aby uzyskać więcej informacji, zobacz [Publikowanie projektów usług Azure Cloud Services przy użyciu programu Visual Studio](https://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Gdy wszystko będzie gotowe do wdrożenia aplikacji platformy Azure, sprawdź, czy obiekty docelowe kompilacji projektu są ustawione na **debugowanie**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję projekt, a następnie z menu kontekstowego wybierz pozycję **Publikuj**.
   
1. W oknie dialogowym **publikowanie aplikacji platformy** Azure wybierz subskrypcję platformy Azure, a **następnie**wybierz pozycję Dalej.

1. Na stronie **Ustawienia** wybierz kartę **Ustawienia zaawansowane** .

1. Włącz opcję **Włącz IntelliTrace** , aby zbierać dzienniki IntelliTrace dla aplikacji po opublikowaniu jej w chmurze.
   
1. Aby dostosować podstawową konfigurację IntelliTrace, wybierz pozycję **Ustawienia** obok pozycji **Włącz IntelliTrace**.

    ![Link ustawienia funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. W oknie dialogowym **Ustawienia IntelliTrace** można określić, które zdarzenia mają być rejestrowane, w jaki sposób zbierać informacje o wywołaniach, moduły i procesy do zbierania dzienników oraz ilość miejsca przydzielonego do nagrania. Aby uzyskać więcej informacji na temat IntelliTrace, zobacz [debugowanie z IntelliTrace](https://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Ustawienia funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Dziennik funkcji IntelliTrace jest cyklicznego pliku dziennika maksymalnego rozmiaru określonego w ustawieniach funkcji IntelliTrace (domyślny rozmiar to 250 MB). Dzienniki funkcji IntelliTrace są zbierane do pliku w systemie plików maszyny wirtualnej. W przypadku żądania dzienniki, migawki jest wykonywane w danym momencie i pobrany na komputer lokalny.

Po opublikowaniu usługi w chmurze platformy Azure na platformie Azure Możesz określić, czy IntelliTrace został włączony z poziomu węzła platformy Azure w **Eksplorator serwera**, jak pokazano na poniższej ilustracji:

![Server Explorer — funkcja IntelliTrace jest włączony](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Pobierz dzienniki IntelliTrace dla wystąpienia roli
W programie Visual Studio można pobrać dzienników IntelliTrace dla wystąpienia roli wykonaj następujące czynności:

1. W **Eksplorator serwera**rozwiń węzeł **Cloud Services** i zlokalizuj wystąpienie roli, którego dzienniki chcesz pobrać. 

1. Kliknij prawym przyciskiem myszy wystąpienie roli, a następnie z menu kontekstowego s wybierz opcję **Wyświetl dzienniki IntelliTrace**. 

    ![Wyświetlanie opcji menu Dzienniki funkcji IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Dzienniki IntelliTrace są pobierane do pliku w katalogu na komputerze lokalnym. Rejestruje każdorazowo zażądania IntelliTrace, jest tworzona nowa migawka. Podczas pobierania dzienników program Visual Studio wyświetla postęp operacji w oknie **Dziennik aktywności platformy Azure** . Jak pokazano na poniższej ilustracji, można rozwinąć element wiersza dla operacji wyświetlić więcej szczegółów.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Możesz kontynuować pracę w programie Visual Studio, podczas pobierania dzienników IntelliTrace. Dziennik zakończył pobieranie, zostanie otwarty w programie Visual Studio.

> [!NOTE]
> Dzienniki IntelliTrace może zawierać wyjątki, które generuje platformę i obsługuje go później. Wewnętrzną strukturę kod generuje te wyjątki, jako część normalnego uruchamiania roli, dzięki czemu można je bezpiecznie zignorować.
> 
> 

## <a name="next-steps"></a>Kolejne kroki
- [Opcje debugowania usług Azure Cloud Services](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikowanie usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)