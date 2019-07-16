---
title: Skonfiguruj zaporę Windows zdalne debugowanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f41aa8c074f724976adabaa99df0e8ca0064fa3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161541"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób skonfigurowania zapory w celu włączenia debugowania zdalnego na komputerach z następującymi systemami operacyjnymi:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 z dodatkiem R2  
  
  Jeśli sieci, na którym jest debugowany, nie są chronione przez zaporę, ta konfiguracja nie jest konieczne. W przeciwnym razie komputer, który jest hostem programu Visual Studio i komputera zdalnego, który ma być debugowany wymagają zmian w konfiguracji zapory.  
  
  **Protokół IPSec** Jeśli sieć wymaga tej komunikacji jest wykonywane za pomocą protokołu IPSec, należy otworzyć dodatkowe porty na komputerze-hoście programu Visual Studio i komputera zdalnego.  
  
  **Serwer sieci Web** przypadku debugowania zdalnego serwera sieci Web, należy otworzyć port dodatkowy na komputerze zdalnym.  
  
  Należy pamiętać, że oba komputery pracują jest konieczne uruchomienie tego samego systemu operacyjnego. Na przykład komputer z programem Visual Studio może działać system Windows 10 i komputer zdalny można uruchomić system Windows Server 2012 R2.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Aby skonfigurować zaporę Windows na komputerze programu Visual Studio  
 Instrukcje dotyczące konfigurowania zapory Windows się nieznacznie różnić w różnych systemach operacyjnych. Windows 7 lub Windows Server 2008, słowo **program** jest używany; w systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany.  W poniższych krokach używamy słowa **aplikacji**.  
  
1. Otwórz stronę zapory Windows. (W **Start** polu wyszukiwania menu, typ **zapory Windows**).  
  
2. Kliknij przycisk **Zezwalaj aplikacji lub funkcję przez zaporę Windows**.  
  
3. W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **Visual Studio zdalnego debugera odnajdywania**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczone, a także wybrano jeden lub więcej typów sieci.  
  
4. Jeśli **Visual Studio zdalnego debugera odnajdywania** jest wymieniony, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie widać go w **Dodaj aplikację** okna, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5. W **dozwolone aplikacje i funkcje** listy wybierz **zdalny Monitor debugowania Visual Studio**. Zaznacz jeden lub więcej typów sieci (**domeny głównej/pracy (prywatny), publiczne**) ma monitor debugera zdalnego nawiązać połączenia z usługą. Typy mogą zawierać sieci, do którego jest podłączony komputer z programem Visual Studio.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Aby otworzyć port na komputerze programu Visual Studio, aby włączyć odnajdywanie  
 Musisz zezwolić na porcie UDP 3702 przychodzących umożliwić wykrycie komputerów uruchomienie zdalnego debugera. Aby dodać go, zobacz jak konfigurowanie portów w zaporze.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Aby skonfigurować zaporę Windows komputera zdalnego do zdalnego debugowania  
 Składniki zdalnego debugowania można zainstalowane na komputerze zdalnym lub uruchom z udostępnionego katalogu. W obu przypadkach należy skonfigurować zapory komputera zdalnego. Składniki debugowania zdalnego znajdują się w:  
  
 **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Remote debugera**  
  
 Instrukcje dotyczące konfigurowania zapory Windows się nieznacznie różnić w różnych systemach operacyjnych. Windows 7 lub Windows Server 2008, słowo **program** jest używany; w systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany.  W poniższych krokach używamy słowa **aplikacji**.  
  
1. Otwórz stronę zapory Windows. (Na **Start** polu wyszukiwania menu, typ **zapory Windows**.)  
  
2. Kliknij przycisk **Zezwalaj aplikacji lub funkcję przez zaporę Windows**.  
  
3. W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **zdalny Monitor debugowania Visual Studio**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczone, a także wybrano jeden lub więcej typów sieci.  
  
4. Jeśli **zdalny Monitor debugowania Visual Studio** jest wymieniony, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie widać go w **okno aplikacji Dodaj**, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5. W **dozwolone aplikacje** listy wybierz **zdalny Monitor debugowania Visual Studio**. Zaznacz jeden lub więcej typów sieci (**domeny głównej/pracy (prywatny), publiczne**) ma monitor debugera zdalnego nawiązać połączenia z usługą. Typy mogą zawierać sieci, do którego jest podłączony komputer z programem Visual Studio.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, na które Włączanie debugowania zdalnego  
  
|||||  
|-|-|-|-|  
|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|  
|3702|Wychodzące|UDP|Wymagana w przypadku odnajdywania zdalnego debugera.|  
|4020||TCP|Dla programu VS 2015. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji zobacz Visual przypisania portów debugera zdalnego Studio.|  
|4021||TCP|Dla programu VS 2015. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji zobacz Visual przypisania portów debugera zdalnego Studio.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Porty na komputerze zdalnym, które umożliwiają zdalne debugowanie w trybie zgodności zarządzane lub natywne  
  
|||||  
|-|-|-|-|  
|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|  
|135, 139, 445|Wychodzące|TCP|Wymagana.|  
|137, 138|Wychodzące|UDP|Wymagane.|  
|500, 4500|Wychodzące|UDP|Wymagane, jeśli zasady domeny wymaga komunikacji sieciowej, można wykonać przy użyciu protokołu IPSec.|  
|80|Wychodzące|TCP|Wymagane na potrzeby debugowania na serwerze sieci Web.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Jak skonfigurować porty w Zaporze Windows  
  
1. Na **Start** menu, wyszukaj **Zapora Windows z zabezpieczeniami zaawansowanymi**.  
  
2. Kliknij przycisk **reguły ruchu przychodzącego** lub **reguł dla ruchu wychodzącego** a następnie kliknij przycisk **nową regułę** w **akcje** listy.  
  
3. Na **typ reguły** wybierz opcję **portu** a następnie kliknij przycisk **dalej**.  
  
4. Na **protokół i porty** wybierz portu i protokołu (TCP lub UDP). Wybierz **określone porty lokalne** i wprowadź numery portów, które chcesz włączyć dla protokołu. Oddzielne numery przecinkami. Następnie kliknij przycisk **Dalej**.  
  
5. Na **akcji** wybierz opcję **Zezwalaj na połączenie** a następnie kliknij przycisk **dalej**.  
  
6. Na **profilu** wybierz jeden lub więcej typów sieci, aby włączyć za pośrednictwem portu usługi. Wybranego typu musi zawierać sieci, do którego jest podłączony komputera zdalnego. Następnie kliknij przycisk **Dalej**.  
  
7. Na **nazwa** stronie, wpisz nazwę reguły, a następnie kliknij **Zakończ**.  
  
8. Powinien zostać wyświetlony nową regułę w **reguły ruchu przychodzącego** lub **reguł dla ruchu wychodzącego** listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
