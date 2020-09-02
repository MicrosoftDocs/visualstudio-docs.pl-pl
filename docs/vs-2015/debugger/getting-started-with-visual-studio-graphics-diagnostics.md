---
title: Wprowadzenie z Diagnostyka grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704706"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do diagnostyki grafiki w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji utworzysz Diagnostyka grafiki po raz pierwszy, następnie przechwytuje ramki z aplikacji Direct3D i przeanalizuje je w analizatorze grafiki.

## <a name="requirements"></a>Wymagania
 Aby użyć Diagnostyka grafiki w programie Visual Studio 2015, musisz mieć jedną z następujących wersji:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Społeczność programu Visual Studio 2015

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Wymagania wstępne dotyczące systemu Windows 10
 Opcjonalne *narzędzia graficzne* funkcji systemu Windows zapewniają infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez Diagnostyka grafiki w systemie Windows 10.

 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [Instalowanie narzędzi graficznych dla systemu Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Wymagania wstępne Windows 8.1
 Zestaw Windows Software Development Kit (SDK) dla Windows 8.1 udostępnia infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez Diagnostyka grafiki w Windows 8.1 i obsługuje programowanie dla Windows 8.1 i systemu Windows 8.

 [Pobierz zestaw Windows Software Development Kit (SDK) dla programu Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Aby użyć komputera z odtwarzaniem zdalnym z systemem Windows 10 z maszyny deweloperskiej z systemem Windows 8.1, należy zainstalować zestaw SDK systemu Windows 10 na komputerze deweloperskim oraz opcjonalną funkcję narzędzi graficznych na komputerze odtwarzającego.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalowanie narzędzi graficznych dla systemu Windows 10
 W systemie Windows 10 Infrastruktura Diagnostyka grafiki jest udostępniana przez opcjonalną funkcję systemu Windows o nazwie *narzędzia graficzne*. Ta funkcja jest wymagana do przechwytywania i odtwarzania informacji graficznych w systemie Windows 10, niezależnie od tego, czy przechwycona aplikacja jest przeznaczona dla poprzedniej wersji systemu Windows, czy używanej wersji programu Direct3D. Możesz wcześniej zainstalować funkcję narzędzi graficznych. w przeciwnym razie zostanie ona zainstalowana na żądanie przy pierwszym uruchomieniu sesji Diagnostyka grafiki z poziomu programu Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzia graficzne dla systemu Windows 10

1. W menu **Start** wybierz pozycję **Ustawienia**. Zostanie wyświetlone okno dialogowe **Ustawienia** .

2. W oknie dialogowym **Ustawienia** wybierz opcję **system**, a następnie na liście ustawień systemowych wybierz pozycję **zainstalowane aplikacje** .

3. Po prawej stronie okna dialogowego **Ustawienia** wybierz pozycję **Zarządzaj funkcjami opcjonalnymi** w obszarze **zainstalowane aplikacje i funkcje**. Zostanie wyświetlone okno dialogowe **Zarządzanie funkcjami opcjonalnymi** .

4. W oknie dialogowym **Zarządzanie funkcjami opcjonalnymi** wybierz pozycję **Dodaj funkcję**. Zostanie wyświetlona lista opcjonalnych funkcji, które można zainstalować.

5. Wybierz pozycję **narzędzia graficzne** z listy funkcje, a następnie wybierz pozycję **Zainstaluj**.

   Funkcja narzędzi graficznych jest również instalowana automatycznie podczas instalacji zestawu Windows 10 SDK.

> [!TIP]
> Opcjonalna funkcja narzędzi graficznych systemu Windows 10 zapewnia uproszczoną funkcję przechwytywania i odtwarzania, taką jak program do przechwytywania wiersza polecenia **dxcap.exe**— który może być używany w scenariuszach obsługi, testowania i diagnostyki na maszynach, na których nie zainstalowano narzędzi deweloperskich. Aby uzyskać więcej informacji, zobacz temat [Narzędzie do przechwytywania wiersza polecenia](../debugger/command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie Diagnostyka grafiki po raz pierwszy
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz zacząć korzystać z Diagnostyka grafiki. Wystarczy wykonać poniższe czynności.

### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji Direct3D
 Jeśli masz już swoją aplikację Direct3D do eksplorowania Diagnostyka grafiki za pomocą programu, świetnie! W przeciwnym razie możesz użyć jednego z przykładów Direct3D dostępnych w galerii kodu.

- Aby wypróbować Diagnostyka grafiki z programem Direct3D 12 w systemie Windows 10 przy użyciu programu Visual Studio 2015, wypróbuj [próbkę Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla systemu Windows 10.

- Aby wypróbować Diagnostyka grafiki z programem Direct3D 11 w systemie Windows 10 lub Windows 8.1, można użyć szablonów projektu **aplikacji DirectX (Windows Universal)** lub  **DirectX (Windows 8.1)** . Lub, aby coś bardziej interesującego, wypróbuj [próbkę gry DirectX marmur labiryntu](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) dla Windows 8.1.

  Przed przejściem do programu upewnij się, że możesz skompilować aplikację.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 — Uruchamianie sesji Diagnostyka grafiki
 Teraz wszystko jest gotowe do rozpoczęcia pierwszej sesji diagnostyki grafiki. W programie Visual Studio w menu głównym wybierz kolejno opcje **Debuguj, grafika, Uruchom diagnostykę**lub po prostu naciśnij klawisze **Alt + F5**. Spowoduje to uruchomienie aplikacji w obszarze Diagnostyka grafiki i wyświetlenie okien sesji diagnostyki w programie Visual Studio.

> [!IMPORTANT]
> Jeśli uruchamiasz aplikację w systemie Windows 10 i nie zainstalowano jeszcze opcjonalnych narzędzi graficznych, zostanie wyświetlony monit o to, aby to zrobić teraz. Należy ją zainstalować przed użyciem Diagnostyka grafiki w systemie Windows 10.

### <a name="3---capture-frames"></a>3 — Przechwyć ramki
 Możesz teraz przechwycić ramki zaraz po uruchomieniu aplikacji.

##### <a name="to-capture-single-frames"></a>Aby przechwycić pojedyncze ramki

- W programie Visual Studio wybierz przycisk **przechwytywania ramki** z paska narzędzi grafiki lub okna sesji diagnostyki. Lub, jeśli aplikacja ma fokus, po prostu naciśnij przycisk **Print Screen**.

##### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencję ramek

- W programie Visual Studio, w oknie sesji diagnostycznej, ustaw **ramki do przechwycenia** do liczby ramek, które mają być przechwytywane w sekwencji, a następnie Przechwyć sekwencję przy użyciu dowolnej metody opisanej powyżej do przechwytywania pojedynczych ramek.

   Aby ponownie przechwycić pojedyncze klatki, ustaw **ramki do przechwycenia** `1` .

  Po zakończeniu przechwytywania ramek wystarczy zamknąć aplikację lub wybrać przycisk **Zatrzymaj** na pasku narzędzi grafiki lub oknie sesji diagnostycznej.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 — Badaj przechwycone ramki w analizatorze grafiki
 Teraz możesz już przechwycić przechwycone ramki. Aby rozpocząć analizowanie ramki, wybierz numer ramki ramki, którą chcesz przeanalizować z okna sesji diagnostycznej. Spowoduje to otwarcie ramki w **analizatorze grafiki**, w której można użyć narzędzi Diagnostyka grafiki, aby sprawdzić, w jaki sposób aplikacja korzysta z Direct3D do śledzenia problemów z renderowaniem, lub użyć narzędzia do **analizy klatek** , aby zrozumieć jego wydajność.

 Jeśli wybrano niewłaściwą ramkę z okna sesji diagnostycznej lub chcesz przejrzeć inną ramkę, możesz wybrać nową klatkę z analizatora grafiki. Na karcie **obiekt docelowy renderowania** okna dziennik grafiki w obszarze obraz elementu docelowego renderowania rozwiń **listę ramka** , a następnie wybierz inną ramkę do sprawdzenia.

 Aby dowiedzieć się więcej o tym, jak używać narzędzi Analizator grafiki, zobacz [przykłady](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Zobacz też
 [Grafika Direct3D 12](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
