---
title: Rejestrowanie zdarzeń dla rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8064c36b6b0e567f868fee7212560d726bbd3c66
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647961"
---
# <a name="event-logging-for-office-solutions"></a>Rejestrowanie zdarzeń dla rozwiązań pakietu Office
  Aby wyświetlić komunikaty o wyjątkach, które są przechwytywane przez służy Podgląd zdarzeń w Windows [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Te komunikaty z Rejestratora zdarzeń służy do instalacji i problemy z wdrażaniem.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="read-the-event-log"></a>Odczytać dziennika zdarzeń  
 Otwórz **Podgląd zdarzeń** i filtrowanie zdarzeń mają być wyświetlane.  
  
### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Można odczytać dziennika zdarzeń w systemie Windows Server 2003 i Windows XP  
  
1.  W Panelu sterowania otwórz **narzędzia administracyjne**.  
  
2.  Rozpocznij **Podgląd zdarzeń**.  
  
3.  Na liście dzienniki zdarzeń, wybierz **aplikacji**.  
  
4.  Na **widoku** menu, kliknij przycisk **filtru**.  
  
5.  W **źródła zdarzeń** listy wybierz **VSTO 4.0**.  
  
6.  W przypadku zdarzeń instalacji w **identyfikator zdarzenia** wpisz **4096**.  
  
7.  Kliknij przycisk **OK** Aby wyświetlić widok filtrowany.  
  
### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Można odczytać dziennika zdarzeń w Windows 7, Windows Vista i Windows Server 2008  
  
1. W Panelu sterowania otwórz **narzędzia administracyjne**.  
  
2. Rozpocznij **Podgląd zdarzeń**.  
  
3. Rozwiń **Dzienniki Windows**.  
  
4. Na liście dzienniki zdarzeń, wybierz **aplikacji**.  
  
5. Na **akcji** menu, kliknij przycisk **Filtruj bieżący dziennik**.  
  
6. W **źródła zdarzeń** listy wybierz **VSTO 4.0**.  
  
7. W przypadku zdarzeń instalacji w **identyfikator zdarzenia** wpisz **4096**.  
  
8. Kliknij przycisk **OK** Aby wyświetlić widok filtrowany.  
  
   Podgląd zdarzeń zawiera następujące informacje:  
  
- Lokalizacja manifestu wdrażania rozwiązania.  
  
- Komunikat, który opisuje przyczynę błąd lub wyjątek.  
  
  Te komunikaty o wyjątkach może pomóc zidentyfikować przyczynę problemu z instalacją, takie jak niezaufany certyfikat, z lokalizacją dokumentu niezaufanych lub manifest nieprawidłowa wdrożenia.  
  
  Po odinstalowaniu rozwiązań pakietu Office, komunikaty o wyjątkach pozostają w dzienniku zdarzeń.  
  
  Aby wyświetlić lub dziennika komunikaty o wyjątkach, gdy działa rozwiązań pakietu Office, zobacz [projekty Office debugowania](../vsto/debugging-office-projects.md) i [projekty Office debugowania](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Lokalizacja  
 Język komunikat o wyjątku jest określany przez Visual Studio Tools for Office runtime języka. Na przykład jeśli na komputerze użytkownika końcowego jest zainstalowany pakiet języka japońskiego, komunikat o wyjątku są zapisywane w dzienniku zdarzeń w języku japońskim.  
  
## <a name="disable-the-event-logger"></a>Wyłączanie rejestrowania zdarzeń  
 Domyślnie program rejestrujący zdarzenia jest włączona podczas instalowania lub odinstalowania rozwiązań pakietu Office. Program rejestrujący zdarzenia można wyłączyć przez ustawienie zmiennej środowiskowej VSTO_EVENTLOGDISABLED "1" (jeden).  
  
### <a name="to-disable-the-event-log"></a>Aby wyłączyć w dzienniku zdarzeń  
  
1.  W Panelu sterowania otwórz **systemu**.  
  
2.  Na **zaawansowane** kliknij pozycję **zmienne środowiskowe**.  
  
3.  W **zmiennych systemowych** okienku kliknij **New**.  
  
4.  W **Nowa zmienna systemowa** okno dialogowe, typ **VSTO_EVENTLOGDISABLED** w **nazwa zmiennej** pole.  
  
5.  W **wartość zmiennej** wpisz **1**.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Rozwiązywanie problemów z wdrażaniem rozwiązań Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  