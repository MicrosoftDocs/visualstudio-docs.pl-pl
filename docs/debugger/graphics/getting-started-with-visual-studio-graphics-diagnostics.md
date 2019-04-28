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
ms.openlocfilehash: 4fc7dd207a525eaed12db1b2e45e7720d96ee8b6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388693"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do diagnostyki grafiki w programie Visual Studio
W tej sekcji umożliwią przygotowanie skorzystać z Graphics Diagnostics po raz pierwszy, a następnie można przechwycić ramki na podstawie aplikacja Direct3D i zbadać je w analizatorze grafiki.

## <a name="requirements"></a>Wymagania
 Aby skorzystać z diagnostyki grafiki w programie Visual Studio, należy użyć programu Visual Studio Enterprise, Visual Studio Professional lub Visual Studio Community.  Inne wersje, w tym Visual Studio Code, nie zawierają tej funkcji.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Wymagania wstępne systemu Windows 10
 Opcjonalna funkcja Windows *narzędzi graficznych* udostępnia infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez narzędzie Diagnostyka grafiki w systemie Windows 10.

 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [zainstalować grafiki Tools for Windows 10](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a> Instalowanie narzędzi graficznych dla systemu Windows 10
 W systemie Windows 10 infrastruktury diagnostyki grafiki świadczą opcjonalna funkcja systemu Windows o nazwie *narzędzi graficznych*. Ta funkcja jest wymagana do przechwytywania i odtwarzania informacji graficznych w systemie Windows 10 niezależnie od tego, czy aplikacja przechwytywanym cele poprzedniej wersji systemu windows lub z wersji Direct3D używa. Istnieje możliwość zainstalowania funkcji narzędzia graficzne wcześniejsze; w przeciwnym razie będzie zainstalowanych na żądanie pierwszy po uruchomieniu sesji diagnostyki grafiki w programie Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzi graficznych dla systemu Windows 10

1. W polu wyszukiwania wpisz **aplikacje i funkcje** , a następnie otwórz **aplikacje i funkcje** ustawienia.

2. W prawej części **aplikacje i funkcje** okno dialogowe, wybierz **Zarządzaj funkcjami opcjonalnymi** (w obszarze **aplikacje i funkcje**).

   **Zarządzaj funkcjami opcjonalnymi** zostanie wyświetlone okno dialogowe.

3. W **Zarządzaj funkcjami opcjonalnymi** okno dialogowe, wybierz **Dodaj funkcję**. Zostanie wyświetlona lista funkcji opcjonalnych, które można zainstalować.

4. Wybierz **narzędzi graficznych** z listy funkcji, następnie wybierz **zainstalować**.

   Funkcja narzędzi graficznych jest również instalowany automatycznie podczas instalacji zestawu Windows 10 SDK.

> [!TIP]
> Opcjonalna funkcja narzędzi graficznych w systemu Windows 10 oferuje uproszczone przechwytywanie i odtwarzanie funkcje — takie jak program wiersza polecenia do przechwytywania **dxcap.exe**— które mogą być używane w pomocy technicznej, testowania i diagnostycznych scenariusze maszyny, na którym nie są zainstalowane narzędzia dla deweloperów. Aby uzyskać więcej informacji, zobacz [narzędzia wiersza polecenia do przechwytywania](command-line-capture-tool.md) tematu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie Graphics Diagnostics po raz pierwszy
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz rozpocząć korzystanie z diagnostyki grafiki. Po prostu wykonaj następujące kroki.

### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji programu Direct3D
 Jeśli masz już własną aplikację Direct3D diagnostyki grafiki, zapoznaj się z świetne! W przeciwnym razie użyj jednej z następujących czynności:

- **Aplikacja programu DirectX 11 (Windows Universal)** lub **DirectX 12 aplikacji (Windows Universal)** szablony projektów dla systemu Windows 10.
- [Przykładowy program Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla systemu Windows 10.

  Upewnij się, że możesz tworzyć aplikacji przed kontynuowaniem.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 — uruchamianie sesji diagnostyki grafiki
 Teraz możesz uruchomić sesję pierwszy diagnostyki grafiki. W programie Visual Studio, w menu głównym wybierz **debugowanie, grafiki, Rozpocznij debugowanie grafiki**, lub po prostu naciśnij **klawisze Alt + F5**. Spowoduje to uruchomienie aplikacji w obszarze Diagnostyka grafiki i wyświetla okien sesji diagnostyki w programie Visual Studio.

> [!IMPORTANT]
> Jeśli Twoja aplikacja działa w systemie Windows 10 i nie został jeszcze zainstalowany opcjonalna funkcja narzędzi graficznych, monit będzie Zrób to teraz. Należy go zainstalować, aby skorzystać z Graphics Diagnostics, w systemie Windows 10.

### <a name="3---capture-frames"></a>3 — przechwytywanie ramek
 Możesz przechwycić ramki, zaraz po uruchomieniu aplikacji.

#### <a name="to-capture-single-frames"></a>Aby przechwycić ramki pojedynczego

- W programie Visual Studio, wybierz **Przechwyć ramkę** przycisk paska narzędzi lub Diagnostyka sesji okna grafiki. Lub, jeśli aplikacja ma fokus, wystarczy nacisnąć klawisz **klawisza Print Screen** kluczowe na klawiaturze.

#### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencji ramek

- W programie Visual Studio, w oknie sesji diagnostycznej ustaw **ramek do przechwycenia** do liczby klatek, które mają być przechwytywane w sekwencji, następnie przechwycić sekwencji przy użyciu dowolnej z metod opisanych powyżej, aby przechwycić ramki pojedynczego.

   Aby przechwycić ramki pojedynczego ponownie, należy ustawić **ramek do przechwycenia** do *1*.

  Gdy wszystko będzie gotowe przechwytywanie ramek po prostu zamknąć aplikację, lub wybierz **zatrzymać** przycisk paska narzędzi graficznych lub okna sesji diagnostycznej.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 — Sprawdź przechwycone ramki w analizatorze grafiki
 Teraz możesz przystąpić do sprawdzenia ramki, który został przechwycony. Aby zacząć analizować ramkę, wybierz numer ramki ramki, który chcesz zbadać z okna sesji diagnostycznej. Spowoduje to otwarcie ramki w **analizatora grafiki**, gdzie można użyj narzędzi programu Graphics Diagnostics, aby sprawdzić, jak aplikacja używa technologii Direct3D do śledzenia problemów z renderowaniem, lub użyj **analizy klatek** narzędzia, aby Dowiedz się, jego wydajność.

 Jeśli wybrano niewłaściwy ramce w oknie sesji diagnostycznej lub do innej ramki, można wybrać nową z analizatora grafiki do sprawdzenia. Na **docelowego renderowania** Rozwiń okno dziennika grafiki, w ramach renderowania obrazu docelowego, na karcie **lista ramek** , a następnie wybierz innej ramki do sprawdzenia.

 Aby dowiedzieć się więcej o sposobie używania narzędzia Analizator grafiki programu ze sobą, zobacz [przykłady](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Zobacz też
- [Direct3D 12 grafiki](/windows/desktop/direct3d12/direct3d-12-graphics)