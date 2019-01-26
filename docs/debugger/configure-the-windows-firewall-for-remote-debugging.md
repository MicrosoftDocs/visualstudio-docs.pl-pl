---
title: Konfigurowanie zapory Windows w celu debugowania zdalnego | Dokumentacja firmy Microsoft
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65bb894d705f87d16fc7a6cf9fd446c726db9c92
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039478"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Konfigurowanie zapory Windows w celu debugowania zdalnego

W sieci, chronione przez zaporę Windows zapory musi być skonfigurowany, aby zezwolić na zdalne debugowanie. Visual Studio i narzędzia do debugowania zdalnego próbuje otworzyć porty zapory podczas instalacji lub uruchomienia, ale może być również konieczne otwarcie portów lub aplikacjom ręcznie. 

W tym temacie opisano, jak skonfigurować zaporę Windows, aby włączyć zdalne debugowanie w systemie Windows 10, 8/8.1 i 7; i Windows Server 2012 R2, 2012 r. i 2008 R2 komputery. Visual Studio i komputerem zdalnym nie trzeba korzystać z tego samego systemu operacyjnego. Na przykład komputer z programem Visual Studio może działać system Windows 10 i komputer zdalny można uruchomić system Windows Server 2012 R2.      
  
>[!NOTE]
>Instrukcje dotyczące konfigurowania zapory Windows się nieznacznie różnić w różnych systemach operacyjnych i dla starszych wersji systemu Windows. Ustawienia systemu Windows 8/8.1, Windows 10 i Windows Server 2012 należy użyć słowa *aplikacji*, podczas gdy Windows 7 i Windows Server 2008 należy użyć słowa *program*.  

## <a name="configure-ports-for-remote-debugging"></a>Skonfiguruj porty dla zdalnego debugowania  

Program Visual Studio i zdalnym debugerem spróbuj otworzyć porty podczas instalacji lub uruchomienia. Jednak w niektórych scenariuszach, takich jak zapory innych firm, może być konieczne ręcznie otworzyć porty. 

**Aby otworzyć port:**
  
1. W Windows **Start** menu Wyszukaj i Otwórz **Zapora Windows z zabezpieczeniami zaawansowanymi**. W systemie Windows 10 to **zapory Windows Defender z zabezpieczeniami zaawansowanymi**.
   
1. Wybierz nowy port przychodzący **reguły ruchu przychodzącego** , a następnie wybierz **nową regułę**. Wychodzące reguły, wybierz **reguł dla ruchu wychodzącego** zamiast tego.

1. W **Kreatora nowej reguły przychodzącej**, wybierz opcję **portu**, a następnie wybierz pozycję **dalej**. 
   
1. Wybierz opcję **TCP** lub **UDP**, w zależności od numeru portu z następujących tabel.
   
1. W obszarze **określone porty lokalne**, wprowadź numer portu z następujących tabel i wybierz **dalej**.
   
1. Wybierz **Zezwalaj na połączenie**, a następnie wybierz pozycję **dalej**.
   
1. Wybierz co najmniej jeden typ sieci, aby włączyć, łącznie z typem sieci dla połączenia zdalnego, a następnie wybierz **dalej**.
   
1. Dodaj nazwę reguły (na przykład **msvsmon**, **usług IIS**, lub **narzędzia Web Deploy**), a następnie wybierz pozycję **Zakończ**.

   Nowa reguła powinny być wyświetlane i można wybrać w **reguły ruchu przychodzącego** lub **reguł dla ruchu wychodzącego** listy.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, na które Włączanie debugowania zdalnego

Zdalne debugowanie, muszą być otwarte na komputerze zdalnym następujące porty:

|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|   
|-|-|-|-|
|4022|przychodzące|TCP|Dla programu VS 2017. Zwiększa numer portu przez 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).|  
|4023|przychodzące|TCP|Dla programu VS 2017. Zwiększa numer portu przez 2 dla każdej wersji programu Visual Studio. Ten port jest tylko używany do zdalnego debugowania 32-bitowy proces z 64-bitowej wersji zdalnego debugera. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).| 
|3702|Wychodzące|UDP|(Opcjonalnie) Wymagana w przypadku odnajdywania zdalnego debugera.|    
  
Jeśli wybierzesz **Użyj trybu zgodności zarządzanej** w obszarze **narzędzia** > **opcje** > **debugowanie**, otwórz porty te dodatkowe zdalnego debugera. Trybu zgodności zarządzanej debuger umożliwia starszej wersji, wersji debugera programu Visual Studio 2010. 

|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|  
|-|-|-|-|  
|135, 139, 445|Wychodzące|TCP|Wymagana.|  
|137, 138|Wychodzące|UDP|Wymagana.|  

Jeśli zasady domeny wymaga komunikacji sieciowej, można wykonać przy użyciu protokołu IPSec, należy otworzyć dodatkowych portów w programie Visual Studio i komputer zdalny. Aby debugować na zdalnym serwerze sieci web usług IIS, należy otworzyć port 80 na komputerze zdalnym.

|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|  
|-|-|-|-|  
|500, 4500|Wychodzące|UDP|Wymagane, jeśli zasady domeny wymaga komunikacji sieciowej, można wykonać przy użyciu protokołu IPSec.|  
|80|Wychodzące|TCP|Wymagane na potrzeby debugowania na serwerze sieci web.|

Aby zezwolić na wybrane aplikacje przez zaporę Windows, zobacz [Konfiguruj zdalne debugowanie przez zaporę Windows](#configure-remote-debugging-through-windows-firewall). 

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfiguruj zdalne debugowanie przez zaporę Windows

Możesz zainstalować narzędzia do debugowania zdalnego na komputerze zdalnym lub uruchomić je z folderem udostępnionym. W obu przypadkach zapory na komputerze zdalnym musi być prawidłowo skonfigurowane. 

Na komputerze zdalnym narzędzia do debugowania zdalnego należą:  
  
*\<Katalog instalacyjny usługi Visual Studio\>\\Common7\\IDE\\zdalny debuger\\\<x86*, *x64*, lub  *Pakiet Appx*\> 
  
### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Zezwalaj na i skonfigurować zdalny debuger przez zaporę Windows 
  
1. W Windows **Start** menu Wyszukaj i Otwórz **zapory Windows**, lub **zapory Windows Defender**. 
  
1. Wybierz **zezwolenie aplikacji przez zaporę Windows**.  
  
1.  Jeśli **zdalny debuger** lub **zdalny debuger programu Visual Studio** nie pojawia się w obszarze **dozwolone aplikacje i funkcje**, wybierz opcję **zmiany ustawień**, a następnie wybierz pozycję **Zezwalaj na inną aplikację**. 

1.  Jeśli aplikację zdalny debuger nadal nie jest wymieniony w **Dodaj aplikację** okno dialogowe, wybierz opcję **Przeglądaj**i przejdź do  *\<katalogu instalacyjnego programu Visual Studio\> \\Common7\\IDE\\zdalny debuger\\\<x86*, *x64*, lub *Appx* \> , w zależności od architektury właściwej dla aplikacji. Wybierz *msvsmon.exe*, a następnie wybierz pozycję **Dodaj**.  
    
1.  W **aplikacje** listy wybierz **zdalny debuger** , który właśnie został dodany. Wybierz **typy sieci**, a następnie wybierz jeden lub więcej typów sieci, w tym typ sieci dla połączenia zdalnego. 
    
1.  Wybierz **Dodaj**, a następnie wybierz pozycję **OK**.

## <a name="troubleshooting"></a>Rozwiązywanie problemów z połączenia zdalnego debugowania
  
Jeśli nie można dołączyć do aplikacji, za pomocą debugera zdalnego, upewnij się, zdalnego debugowania porty zapory protokoły, typów sieci i ustawienia aplikacji są poprawne. 

- W Windows **Start** menu Wyszukaj i Otwórz **zapory Windows**i wybierz **zezwolenie aplikacji przez zaporę Windows**. Upewnij się, że **zdalny debuger** lub **zdalny debuger programu Visual Studio** pojawia się w **dozwolone aplikacje i funkcje** są listy zaznaczone pole wyboru i typy odpowiedniej sieci wybrany. W przeciwnym razie [Dodaj odpowiednie aplikacje i ustawienia](#configure-remote-debugging-through-windows-firewall).
  
- W Windows **Start** menu Wyszukaj i Otwórz **Zapora Windows z zabezpieczeniami zaawansowanymi**. Upewnij się, że **zdalny debuger** lub **zdalny debuger programu Visual Studio** pojawia się w obszarze **reguły ruchu przychodzącego** (i, opcjonalnie, **reguł dla ruchu wychodzącego**) za pomocą Ikona zielonego znacznika wyboru, a wszystkie ustawienia są poprawne. 
  
  - Aby wyświetlić lub zmienić ustawienia reguł, kliknij prawym przyciskiem myszy **zdalny debuger** aplikacji na liście i wybierz **właściwości**. Użyj **właściwości** kart, aby włączyć lub wyłączyć zasadę lub zmienić port liczb, protokołów lub typów sieci. 
  - Jeśli aplikację zdalny debuger nie jest wyświetlana na liście reguł [dodać i skonfigurować odpowiednie porty](#configure-ports-for-remote-debugging). 

## <a name="see-also"></a>Zobacz także  
[Debugowanie zdalne](../debugger/remote-debugging.md)

[Przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md)
