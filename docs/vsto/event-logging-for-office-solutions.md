---
title: Rejestrowanie zdarzeń dla rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 480a355ee2af321341c54b90edcc582d49102186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951947"
---
# <a name="event-logging-for-office-solutions"></a>Rejestrowanie zdarzeń dla rozwiązań pakietu Office
  Podgląd zdarzeń w systemie Windows może służyć do wyświetlania komunikatów o wyjątkach, które są przechwytywane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program podczas instalowania lub odinstalowywania rozwiązań pakietu Office. Możesz użyć tych komunikatów z rejestratora zdarzeń, aby rozwiązać problemy dotyczące instalacji i wdrażania.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Odczytaj dziennik zdarzeń
 Otwórz **Podgląd zdarzeń** i odfiltruj zdarzenia, które chcesz wyświetlić.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Aby odczytać dziennik zdarzeń w systemie Windows Server 2003 i Windows XP

1. W panelu sterowania otwórz aplet **Narzędzia administracyjne**.

2. Rozpocznij **Podgląd zdarzeń**.

3. Na liście dzienników zdarzeń wybierz pozycję **aplikacja**.

4. W menu **Widok** kliknij polecenie **Filtruj**.

5. Na liście **Źródło zdarzeń** wybierz pozycję **VSTO 4,0**.

6. W przypadku zdarzeń instalacji w polu **Identyfikator zdarzenia** wpisz **4096**.

7. Kliknij przycisk **OK** , aby wyświetlić widok filtrowany.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Aby odczytać dziennik zdarzeń w systemach Windows 7, Windows Vista i Windows Server 2008

1. W panelu sterowania otwórz aplet **Narzędzia administracyjne**.

2. Rozpocznij **Podgląd zdarzeń**.

3. Rozwiń węzeł **Dzienniki systemu Windows**.

4. Na liście dzienników zdarzeń wybierz pozycję **aplikacja**.

5. W menu **Akcja** kliknij polecenie **Filtruj bieżący dziennik**.

6. Na liście **Źródło zdarzeń** wybierz pozycję **VSTO 4,0**.

7. W przypadku zdarzeń instalacji w polu **Identyfikator zdarzenia** wpisz **4096**.

8. Kliknij przycisk **OK** , aby wyświetlić widok filtrowany.

   Podgląd zdarzeń zawiera następujące informacje:

- Lokalizacja manifestu wdrażania dla rozwiązania.

- Komunikat, który opisuje przyczynę błędu lub wyjątku.

  Te komunikaty o wyjątkach mogą pomóc określić przyczynę problemu z instalacją, na przykład niezaufanego certyfikatu, niezaufanej lokalizacji dokumentu lub nieprawidłowego manifestu wdrożenia.

  Po odinstalowaniu rozwiązania pakietu Office komunikaty o wyjątkach pozostają w dzienniku zdarzeń.

  Aby wyświetlać lub rejestrować komunikaty o wyjątkach, gdy jest uruchomione rozwiązanie pakietu Office, zobacz [Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md) i [Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md).

### <a name="localization"></a>Lokalizacja
 Język komunikatu o wyjątku jest określany na podstawie Visual Studio Tools w języku uruchomieniowym pakietu Office. Na przykład jeśli na komputerze użytkownika końcowego jest zainstalowany pakiet języka japońskiego, komunikat o wyjątku jest zapisywana w dzienniku zdarzeń w języku japońskim.

## <a name="disable-the-event-logger"></a>Wyłącz rejestratora zdarzeń
 Domyślnie Rejestrator zdarzeń jest włączany podczas instalowania lub odinstalowywania rozwiązań pakietu Office. Rejestratora zdarzeń można wyłączyć, ustawiając zmienną środowiskową VSTO_EVENTLOGDISABLED na wartość "1" (jeden).

### <a name="to-disable-the-event-log"></a>Aby wyłączyć dziennik zdarzeń

1. W panelu sterowania Otwórz **system**.

2. Na karcie **Zaawansowane** kliknij pozycję **zmienne środowiskowe**.

3. W okienku **zmienne systemowe** kliknij pozycję **Nowy**.

4. W **nowej zmiennej systemowej** okno dialogowe, wpisz **VSTO_EVENTLOGDISABLED** w polu **Nazwa zmiennej** .

5. W polu **wartość zmiennej** wpisz **1**.

6. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Rozwiązywanie problemów z wdrażaniem rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-deployment.md)
