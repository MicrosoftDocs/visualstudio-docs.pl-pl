---
title: Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f232446ed699bd7cc034e4b6d6148b665830cf2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535528"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób konfigurowania zapory w celu włączenia debugowania zdalnego na komputerach z następującymi systemami operacyjnymi:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 z dodatkiem R2  
  
  Jeśli sieć, w której jest debugowany, nie jest chroniona przez zaporę, ta konfiguracja jest niepotrzebna. W przeciwnym razie zarówno komputer obsługujący program Visual Studio, jak i komputer zdalny, który ma być debugowany, wymagają zmian w konfiguracji zapory.  
  
  **Protokół IPSec** Jeśli sieć wymaga przeprowadzania komunikacji przy użyciu protokołu IPSec, należy otworzyć dodatkowe porty zarówno na komputerze hosta programu Visual Studio, jak i na komputerze zdalnym.  
  
  **Serwer sieci Web** W przypadku debugowania zdalnego serwera sieci Web należy otworzyć dodatkowy port na komputerze zdalnym.  
  
  Należy pamiętać, że oba komputery nie muszą uruchamiać tego samego systemu operacyjnego. Na przykład na komputerze z programem Visual Studio można uruchomić system Windows 10, a na komputerze zdalnym można uruchomić system Windows Server 2012 R2.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Aby skonfigurować zaporę systemu Windows na komputerze z Visual Studio  
 Instrukcje dotyczące konfigurowania zapory systemu Windows różnią się nieco w różnych systemach operacyjnych. W systemie Windows 7 lub Windows Server 2008, używany jest **program** Word; w systemie Windows 8/8.1, Windows 10 i Windows Server 2012 jest używana **aplikacja** Word.  W poniższych krokach zostanie użyta **aplikacja**Word.  
  
1. Otwórz stronę Zapora systemu Windows. (W polu wyszukiwania menu **Start** wpisz **Zapora systemu Windows**).  
  
2. Kliknij pozycję **Zezwalaj aplikacji lub funkcji za poorednictwem zapory systemu Windows**.  
  
3. Na liście **dozwolone aplikacje i funkcje** poszukaj **zdalny debuger programu Visual Studio odnajdywania**. Jeśli znajduje się na liście, upewnij się, że jest zaznaczone, a także że wybrano co najmniej jeden typ sieci.  
  
4. Jeśli **odnajdywanie zdalny debuger programu Visual Studio** nie znajduje się na liście, kliknij pozycję **Zezwól na inną aplikację**. Jeśli nadal nie widzisz go w oknie **Dodawanie aplikacji** , kliknij przycisk **Przeglądaj** i przejdź do ** \<Visual Studio installation directory> debugera \Common7\IDE\Remote**. Znajdź odpowiedni folder dla aplikacji (x86, x64, APPX), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5. Na liście **dozwolone aplikacje i funkcje** wybierz pozycję **Visual Studio Monitor zdalnego debugowania**. Sprawdź co najmniej jeden typ sieci (**domena, dom/Work (prywatny), publiczny**), z którym ma być nawiązywane monitorowanie zdalnego debugowania. Typy muszą zawierać sieć, z którą jest połączony komputer z programu Visual Studio.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Aby otworzyć port na komputerze programu Visual Studio w celu włączenia odnajdywania  
 Należy zezwolić na ruch przychodzący portu UDP 3702, aby umożliwić odnajdywanie komputerów z uruchomionym zdalnym debugerem. Aby je dodać, zobacz Jak skonfigurować porty w zaporze.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Aby skonfigurować zaporę systemu Windows komputera zdalnego do zdalnego debugowania  
 Składniki debugowania zdalnego można zainstalować na komputerze zdalnym lub uruchomić z udostępnionego katalogu. Zapora komputera zdalnego musi być skonfigurowana w obu przypadkach. Składniki debugowania zdalnego znajdują się w:  
  
 **\<Visual Studio installation directory>Debuger \Common7\IDE\Remote**  
  
 Instrukcje dotyczące konfigurowania zapory systemu Windows różnią się nieco w różnych systemach operacyjnych. W systemie Windows 7 lub Windows Server 2008, używany jest **program** Word; w systemie Windows 8/8.1, Windows 10 i Windows Server 2012 jest używana **aplikacja** Word.  W poniższych krokach zostanie użyta **aplikacja**Word.  
  
1. Otwórz stronę Zapora systemu Windows. (W polu wyszukiwania menu **Start** wpisz **Zapora systemu Windows**).  
  
2. Kliknij pozycję **Zezwalaj aplikacji lub funkcji za poorednictwem zapory systemu Windows**.  
  
3. Na liście **dozwolone aplikacje i funkcje** Znajdź pozycję **Visual Studio Monitor zdalnego debugowania**. Jeśli znajduje się na liście, upewnij się, że jest zaznaczone, a także że wybrano co najmniej jeden typ sieci.  
  
4. Jeśli **Monitor zdalnego debugowania programu Visual Studio** nie ma na liście, kliknij pozycję **Zezwól na inną aplikację**. Jeśli nadal nie widzisz go w **oknie Dodawanie aplikacji**, kliknij przycisk **Przeglądaj** i przejdź do ** \<Visual Studio installation directory> debugera \Common7\IDE\Remote**. Znajdź odpowiedni folder dla aplikacji (x86, x64, APPX), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5. Na liście **dozwolone aplikacje** wybierz pozycję **Visual Studio Monitor zdalnego debugowania**. Sprawdź co najmniej jeden typ sieci (**domena, dom/Work (prywatny), publiczny**), z którym ma być nawiązywane monitorowanie zdalnego debugowania. Typy muszą zawierać sieć, z którą jest połączony komputer z programu Visual Studio.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, które umożliwiają debugowanie zdalne  
  
|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|  
|-|-|-|-|
|3702|Przeznaczony|UDP|Wymagane do zdalnego odnajdowania debugera.|  
|4020||TCP|Dla programu VS 2015. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz zdalny debuger programu Visual Studio przypisania portów.|  
|4021||TCP|Dla programu VS 2015. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz zdalny debuger programu Visual Studio przypisania portów.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Porty na komputerze zdalnym, które umożliwiają debugowanie zdalne z trybem zgodności zarządzanej lub natywnej  
  
|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|  
|-|-|-|-|  
|135, 139, 445|Przeznaczony|TCP|Wymagany.|  
|137, 138|Przeznaczony|UDP|Wymagany.|  
|500, 4500|Przeznaczony|UDP|Wymagane, jeśli zasady domeny wymagają komunikacji sieciowej za poorednictwem protokołu IPSec.|  
|80|Przeznaczony|TCP|Wymagane do debugowania serwera sieci Web.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Jak skonfigurować porty w zaporze systemu Windows  
  
1. W menu **Start** Wyszukaj pozycję **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.  
  
2. Kliknij pozycję **reguły ruchu przychodzącego** lub **reguły ruchu wychodzącego** , a następnie kliknij pozycję **Nowa reguła** na liście **Akcje** .  
  
3. Na stronie **Typ reguły** wybierz pozycję **port** , a następnie kliknij przycisk **dalej**.  
  
4. Na stronie **Protokół i porty** wybierz protokół port (TCP lub UDP). Wybierz **określone porty lokalne** i wprowadź co najmniej jeden numer portu, który ma zostać włączony dla protokołu. Oddzielaj liczby przecinkami. Następnie kliknij przycisk **Dalej**.  
  
5. Na stronie **Akcja** wybierz opcję **Zezwalaj na połączenie** , a następnie kliknij przycisk **dalej**.  
  
6. Na stronie **profil** wybierz jeden lub więcej typów sieci, które mają być włączone dla portu. Wybrany typ musi zawierać sieć, z którą połączony jest komputer zdalny. Następnie kliknij przycisk **Dalej**.  
  
7. Na stronie **Nazwa** wpisz nazwę reguły, a następnie kliknij przycisk **Zakończ**.  
  
8. Nowa reguła powinna zostać wyświetlona na liście **reguły ruchu przychodzącego** lub **reguły ruchu wychodzącego** .  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
