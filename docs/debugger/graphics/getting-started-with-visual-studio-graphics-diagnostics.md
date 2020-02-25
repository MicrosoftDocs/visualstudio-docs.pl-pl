---
title: Wprowadzenie do diagnostyki grafiki | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575b0254768ac359e43cd5b04c23a220549ac973
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557918"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do diagnostyki grafiki w programie Visual Studio
W tej sekcji umożliwią przygotowanie skorzystać z Graphics Diagnostics po raz pierwszy, a następnie można przechwycić ramki na podstawie aplikacja Direct3D i zbadać je w analizatorze grafiki.

## <a name="requirements"></a>Wymagania
 Aby skorzystać z diagnostyki grafiki w programie Visual Studio, należy użyć programu Visual Studio Enterprise, Visual Studio Professional lub Visual Studio Community.  Inne wersje, w tym Visual Studio Code, nie zawierają tej funkcji.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Wymagania wstępne systemu Windows 10
 Opcjonalne *narzędzia graficzne* funkcji systemu Windows zapewniają infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez Diagnostyka grafiki w systemie Windows 10.

 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [Instalowanie narzędzi graficznych dla systemu Windows 10](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a>Instalowanie narzędzi graficznych dla systemu Windows 10
 W systemie Windows 10 Infrastruktura Diagnostyka grafiki jest udostępniana przez opcjonalną funkcję systemu Windows o nazwie *narzędzia graficzne*. Ta funkcja jest wymagana do przechwytywania i odtwarzania informacji graficznych w systemie Windows 10 niezależnie od tego, czy aplikacja przechwytywanym cele poprzedniej wersji systemu windows lub z wersji Direct3D używa. Istnieje możliwość zainstalowania funkcji narzędzia graficzne wcześniejsze; w przeciwnym razie będzie zainstalowanych na żądanie pierwszy po uruchomieniu sesji diagnostyki grafiki w programie Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzi graficznych dla systemu Windows 10

1. W obszarze wyszukiwania wpisz **aplikacje i funkcje** , a następnie otwórz pozycję **aplikacje & Ustawienia funkcji** .

2. Po prawej stronie ustawień **funkcji & aplikacji** wybierz pozycję **funkcje opcjonalne** (w obszarze **aplikacje & funkcje**).

   Zostaną wyświetlone ustawienia **funkcji opcjonalnych** .

3. W obszarze Ustawienia **funkcji opcjonalnych** wybierz pozycję **Dodaj funkcję**. Zostanie wyświetlona lista funkcji opcjonalnych, które można zainstalować.

4. Wybierz pozycję **narzędzia graficzne** z listy funkcje, a następnie wybierz pozycję **Zainstaluj**.

   Funkcja narzędzi graficznych jest również instalowany automatycznie podczas instalacji zestawu Windows 10 SDK.

> [!TIP]
> Opcjonalna funkcja narzędzi graficznych systemu Windows 10 zapewnia uproszczoną funkcję przechwytywania i odtwarzania, taką jak program do przechwytywania wiersza polecenia **DXCap. exe**— który może być używany w scenariuszach obsługi, testowania i diagnostyki na maszynach, na których nie są zainstalowane narzędzia deweloperskie. Aby uzyskać więcej informacji, zobacz temat [Narzędzie do przechwytywania wiersza polecenia](command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie Graphics Diagnostics po raz pierwszy
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz rozpocząć korzystanie z diagnostyki grafiki. Wystarczy wykonać poniższe czynności.

### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji programu Direct3D
 Jeśli masz już własną aplikację Direct3D diagnostyki grafiki, zapoznaj się z świetne! W przeciwnym razie użyj jednej z następujących czynności:

- Szablony projektów **aplikacji DirectX 11 (uniwersalnego systemu Windows)** lub **DirectX 12** dla systemu Windows 10.
- [Przykład UAP Direct3D 12](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla systemu Windows 10.

  Upewnij się, że możesz tworzyć aplikacji przed kontynuowaniem.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 — uruchamianie sesji diagnostyki grafiki
 Teraz możesz uruchomić sesję pierwszy diagnostyki grafiki. W programie Visual Studio w menu głównym wybierz kolejno opcje **Debuguj, grafika, Rozpocznij debugowanie grafiki**lub po prostu naciśnij klawisze **Alt + F5**. Spowoduje to uruchomienie aplikacji w obszarze Diagnostyka grafiki i wyświetla okien sesji diagnostyki w programie Visual Studio.

> [!IMPORTANT]
> Jeśli Twoja aplikacja działa w systemie Windows 10 i nie został jeszcze zainstalowany opcjonalna funkcja narzędzi graficznych, monit będzie Zrób to teraz. Należy go zainstalować, aby skorzystać z Graphics Diagnostics, w systemie Windows 10.

### <a name="3---capture-frames"></a>3 — przechwytywanie ramek
 Możesz przechwycić ramki, zaraz po uruchomieniu aplikacji.

#### <a name="to-capture-single-frames"></a>Aby przechwycić ramki pojedynczego

- W programie Visual Studio wybierz przycisk **przechwytywania ramki** z paska narzędzi grafiki lub okna sesji diagnostyki. Lub, jeśli aplikacja ma fokus, po prostu naciśnij klawisz **Print Screen** na klawiaturze.

#### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencji ramek

- W programie Visual Studio, w oknie sesji diagnostycznej, ustaw **ramki do przechwycenia** do liczby ramek, które mają być przechwytywane w sekwencji, a następnie Przechwyć sekwencję przy użyciu dowolnej metody opisanej powyżej do przechwytywania pojedynczych ramek.

   Aby ponownie przechwycić pojedyncze klatki, ustaw **ramki do przechwycenia** na *1*.

  Po zakończeniu przechwytywania ramek wystarczy zamknąć aplikację lub wybrać przycisk **Zatrzymaj** na pasku narzędzi grafiki lub oknie sesji diagnostycznej.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 — Sprawdź przechwycone ramki w analizatorze grafiki
 Teraz możesz przystąpić do sprawdzenia ramki, który został przechwycony. Aby zacząć analizować ramkę, wybierz numer ramki ramki, który chcesz zbadać z okna sesji diagnostycznej. Spowoduje to otwarcie ramki w **analizatorze grafiki**, w której można użyć narzędzi Diagnostyka grafiki, aby sprawdzić, w jaki sposób aplikacja korzysta z Direct3D do śledzenia problemów z renderowaniem, lub użyć narzędzia do **analizy klatek** , aby zrozumieć jego wydajność.

 Jeśli wybrano niewłaściwy ramce w oknie sesji diagnostycznej lub do innej ramki, można wybrać nową z analizatora grafiki do sprawdzenia. Na karcie **obiekt docelowy renderowania** okna dziennik grafiki w obszarze obraz elementu docelowego renderowania rozwiń **listę ramka** , a następnie wybierz inną ramkę do sprawdzenia.

 Aby dowiedzieć się więcej o tym, jak używać narzędzi Analizator grafiki, zobacz [przykłady](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Zobacz też
- [Grafika Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)