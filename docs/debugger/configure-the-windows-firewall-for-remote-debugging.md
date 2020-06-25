---
title: Konfigurowanie zapory systemu Windows na potrzeby zdalnego debugowania | Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350696"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego

W sieci chronionej przez zaporę systemu Windows zapora musi być skonfigurowana w taki sposób, aby zezwalała na debugowanie zdalne. Program Visual Studio i narzędzia zdalnego debugowania próbują otworzyć odpowiednie porty zapory podczas instalacji lub uruchamiania, ale może być również konieczne ręczne otwarcie portów lub zezwalanie na aplikacje ręcznie.

W tym temacie opisano sposób konfigurowania zapory systemu Windows w celu umożliwienia zdalnego debugowania w systemie Windows 10, 8/8.1 i 7. Komputery z systemem Windows Server 2012 R2, 2012 i 2008 R2. Program Visual Studio i komputer zdalny nie muszą korzystać z tego samego systemu operacyjnego. Na przykład na komputerze z programem Visual Studio można uruchomić system Windows 10, a na komputerze zdalnym można uruchomić system Windows Server 2012 R2.

>[!NOTE]
>Instrukcje dotyczące konfigurowania zapory systemu Windows różnią się nieco w różnych systemach operacyjnych i w przypadku starszych wersji systemu Windows. Ustawienia systemu Windows 8/8.1, Windows 10 i Windows Server 2012 używają *aplikacji*Word, a systemy Windows 7 i windows Server 2008 używają *programu*Word.

## <a name="configure-ports-for-remote-debugging"></a>Konfigurowanie portów do zdalnego debugowania

Program Visual Studio i zdalny debuger próbują otworzyć odpowiednie porty podczas instalacji lub uruchamiania. Jednak w niektórych scenariuszach, takich jak zapora innej firmy, może być konieczne ręczne otwarcie portów.

**Aby otworzyć port:**

1. W menu **Start** systemu Windows wyszukaj i Otwórz **zaporę systemu Windows z zabezpieczeniami zaawansowanymi**. W systemie Windows 10 jest to **Zapora Windows Defender z zabezpieczeniami zaawansowanymi**.

1. W przypadku nowego portu przychodzącego wybierz pozycję **reguły ruchu przychodzącego** , a następnie wybierz pozycję **Nowa reguła**. Dla reguły wychodzącej wybierz zamiast nich **reguły ruchu wychodzącego** .

1. W **kreatorze Nowa reguła ruchu przychodzącego**wybierz pozycję **port**, a następnie wybierz pozycję **dalej**.

1. Wybierz opcję **TCP** lub **UDP**, w zależności od numeru portu z poniższych tabel.

1. W obszarze **określone porty lokalne**wprowadź numer portu z poniższych tabel, a następnie wybierz przycisk **dalej**.

1. Wybierz opcję **Zezwalaj na połączenie**, a następnie wybierz przycisk **dalej**.

1. Wybierz co najmniej jeden typ sieci do włączenia, w tym typ sieci dla połączenia zdalnego, a następnie wybierz przycisk **dalej**.

1. Dodaj nazwę reguły (na przykład **msvsmon**, **IIS**lub **Web Deploy**), a następnie wybierz pozycję **Zakończ**.

   Nowa reguła powinna zostać wyświetlona i wybrana na liście **reguły ruchu przychodzącego** lub **reguły wychodzące** .

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, które umożliwiają debugowanie zdalne

W przypadku zdalnego debugowania na komputerze zdalnym muszą być otwarte następujące porty:

::: moniker range="vs-2017"

|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|
|-|-|-|-|
|4022|Dane|TCP|Dla programu VS 2017. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Dane|TCP|Dla programu VS 2017. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Ten port jest używany tylko do zdalnego debugowania procesu 32-bitowego z 64-bitowej wersji zdalnego debugera. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Przeznaczony|UDP|Obowiązkowe Wymagane do zdalnego odnajdowania debugera.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|
|-|-|-|-|
|4024|Dane|TCP|Dla programu VS 2019. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Dane|TCP|Dla programu VS 2019. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Ten port jest używany tylko do zdalnego debugowania procesu 32-bitowego z 64-bitowej wersji zdalnego debugera. Aby uzyskać więcej informacji, zobacz [przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Przeznaczony|UDP|Obowiązkowe Wymagane do zdalnego odnajdowania debugera.|

::: moniker-end

W przypadku wybrania opcji **Użyj zarządzanego trybu zgodności** w obszarze **Narzędzia**  >  **Options**  >  **debugowanie**, otwórz te dodatkowe porty zdalnego debugera. Tryb zgodności zarządzany przez debuger umożliwia używanie starszej wersji programu Visual Studio 2010 debugera.

|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|
|-|-|-|-|
|135, 139, 445|Przeznaczony|TCP|Wymagany.|
|137, 138|Przeznaczony|UDP|Wymagany.|

Jeśli zasady domeny wymagają komunikacji sieciowej za pomocą protokołu IPSec, należy otworzyć dodatkowe porty zarówno dla programu Visual Studio, jak i komputerów zdalnych. Aby debugować na zdalnym serwerze sieci Web usług IIS, otwórz port 80 na komputerze zdalnym.

|**Porty**|**Przychodzące/wychodzące**|**Protokół**|**Opis**|
|-|-|-|-|
|500, 4500|Przeznaczony|UDP|Wymagane, jeśli zasady domeny wymagają komunikacji sieciowej za poorednictwem protokołu IPSec.|
|80|Przeznaczony|TCP|Wymagane do debugowania serwera sieci Web.|

Aby zezwolić na określone aplikacje za pomocą zapory systemu Windows, zobacz [Konfigurowanie zdalnego debugowania za pomocą zapory systemu Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfigurowanie zdalnego debugowania za poorednictwem zapory systemu Windows

Narzędzia zdalnego debugowania można zainstalować na komputerze zdalnym lub uruchomić je z folderu udostępnionego. W obu przypadkach Zapora komputera zdalnego musi być poprawnie skonfigurowana.

Na komputerze zdalnym narzędzia debugowania zdalnego znajdują się w:

*\<Visual Studio installation directory\>\\\\ \\ Zdalny debuger IDE Common7\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Zezwalaj i Konfiguruj zdalny debuger za pomocą zapory systemu Windows

1. W menu **Start** systemu Windows wyszukaj i Otwórz **zaporę systemu Windows**lub **zaporę Windows Defender**.

1. Wybierz pozycję **Zezwalaj aplikacji za poorednictwem zapory systemu Windows**.

1. Jeśli **zdalny debuger** lub **zdalny debuger programu Visual Studio** nie jest wyświetlany w obszarze **dozwolone aplikacje i funkcje**, wybierz pozycję **Zmień ustawienia**, a następnie wybierz pozycję **Zezwalaj na inną aplikację**.

1. Jeśli aplikacja Remote Debugger nadal nie znajduje się na liście w oknie dialogowym **Dodawanie aplikacji** , wybierz pozycję **Przeglądaj**, a następnie przejdź do opcji * \<Visual Studio installation directory\> \\ \\ \\ zdalny debuger IDE Common7 \\ \<x86*, *x64*, or *Appx*\> , w zależności od odpowiedniej architektury aplikacji. Wybierz pozycję *msvsmon.exe*, a następnie wybierz pozycję **Dodaj**.

1. Z listy **aplikacje** wybierz **zdalny debuger** , który właśnie został dodany. Wybierz pozycję **typy sieci**, a następnie wybierz jeden lub więcej typów sieci, w tym typ sieci dla połączenia zdalnego.

1. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Rozwiązywanie problemów z połączeniem debugowania zdalnego

Jeśli nie możesz dołączyć do aplikacji ze zdalnym debugerem, upewnij się, że porty zapory zdalnego debugowania, protokoły, typy sieci i ustawienia aplikacji są poprawne.

- W menu **Start** systemu Windows wyszukaj i Otwórz **zaporę systemu Windows**, a następnie wybierz opcję **Zezwalaj aplikacji za pomocą zapory systemu Windows**. Upewnij się, że **zdalny debuger** lub **zdalny debuger programu Visual Studio** pojawia się na liście **dozwolone aplikacje i funkcje** z zaznaczonym polem wyboru, a wybrane są odpowiednie typy sieci. W przeciwnym razie [Dodaj poprawne aplikacje i ustawienia](#configure-remote-debugging-through-windows-firewall).

- W menu **Start** systemu Windows wyszukaj i Otwórz **zaporę systemu Windows z zabezpieczeniami zaawansowanymi**. Upewnij się, że **zdalny debuger** lub **zdalny debuger programu Visual Studio** pojawia się w obszarze **reguły ruchu przychodzącego** (i opcjonalnie **reguły ruchu wychodzącego**) z zieloną ikoną znacznika wyboru i że wszystkie ustawienia są poprawne.

  - Aby wyświetlić lub zmienić ustawienia reguły, kliknij prawym przyciskiem myszy aplikację **Remote Debugger** na liście i wybierz pozycję **Właściwości**. Karta **Właściwości** służy do włączania lub wyłączania reguły, zmieniania numerów portów, protokołów lub typów sieci.
  - Jeśli zdalna aplikacja debugera nie pojawia się na liście reguł, [Dodaj i skonfiguruj odpowiednie porty](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Zobacz też

- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Przypisania portów zdalnego debugera programu Visual Studio](../debugger/remote-debugger-port-assignments.md)
