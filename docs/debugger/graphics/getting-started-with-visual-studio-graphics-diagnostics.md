---
title: Wprowadzenie do diagnostyki grafiki | Microsoft Docs
ms.custom: seodec18
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68cbd19b65eb25405dc994100baf4fddeef9479d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350462"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do diagnostyki grafiki w programie Visual Studio
W tej sekcji utworzysz Diagnostyka grafiki po raz pierwszy, następnie przechwytuje ramki z aplikacji Direct3D i przeanalizuje je w analizatorze grafiki.

## <a name="requirements"></a>Wymagania
 Aby używać Diagnostyka grafiki w programie Visual Studio, musisz użyć Visual Studio Enterprise, Visual Studio Professional lub programu Visual Studio Community.  Inne wersje, w tym Visual Studio Code, nie zawierają tej funkcji.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Wymagania wstępne dotyczące systemu Windows 10
 Opcjonalne *narzędzia graficzne* funkcji systemu Windows zapewniają infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez Diagnostyka grafiki w systemie Windows 10.

 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [Instalowanie narzędzi graficznych dla systemu Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalowanie narzędzi graficznych dla systemu Windows 10
 W systemie Windows 10 Infrastruktura Diagnostyka grafiki jest udostępniana przez opcjonalną funkcję systemu Windows o nazwie *narzędzia graficzne*. Ta funkcja jest wymagana do przechwytywania i odtwarzania informacji graficznych w systemie Windows 10, niezależnie od tego, czy przechwycona aplikacja jest przeznaczona dla poprzedniej wersji systemu Windows, czy używanej wersji programu Direct3D. Możesz wcześniej zainstalować funkcję narzędzi graficznych. w przeciwnym razie zostanie ona zainstalowana na żądanie przy pierwszym uruchomieniu sesji Diagnostyka grafiki z poziomu programu Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzia graficzne dla systemu Windows 10

1. W obszarze wyszukiwania wpisz **aplikacje i funkcje** , a następnie otwórz pozycję **aplikacje & ustawienia funkcji** .

2. Po prawej stronie ustawień **funkcji & aplikacji** wybierz pozycję **funkcje opcjonalne** (w obszarze **aplikacje & funkcje**).

   Zostaną wyświetlone ustawienia **funkcji opcjonalnych** .

3. W obszarze Ustawienia **funkcji opcjonalnych** wybierz pozycję **Dodaj funkcję**. Zostanie wyświetlona lista opcjonalnych funkcji, które można zainstalować.

4. Wybierz pozycję **narzędzia graficzne** z listy funkcje, a następnie wybierz pozycję **Zainstaluj**.

   Funkcja narzędzi graficznych jest również instalowana automatycznie podczas instalacji zestawu Windows 10 SDK.

> [!TIP]
> Opcjonalna funkcja narzędzi graficznych systemu Windows 10 zapewnia uproszczoną funkcję przechwytywania i odtwarzania, taką jak program do przechwytywania wiersza polecenia **dxcap.exe**— który może być używany w scenariuszach obsługi, testowania i diagnostyki na maszynach, na których nie zainstalowano narzędzi deweloperskich. Aby uzyskać więcej informacji, zobacz temat [Narzędzie do przechwytywania wiersza polecenia](command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie Diagnostyka grafiki po raz pierwszy
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz zacząć korzystać z Diagnostyka grafiki. Wystarczy wykonać poniższe czynności.

### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji Direct3D

Jeśli masz już swoją aplikację Direct3D do eksplorowania Diagnostyka grafiki za pomocą programu, świetnie! W przeciwnym razie użyj jednego z następujących elementów:

::: moniker range=">=vs-2019"
Pobierz przykład z [przykładu gry Direct3D](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/simple3dgamedx/).
::: moniker-end
::: moniker range="vs-2017"
- Szablony projektów **aplikacji DirectX 11 (uniwersalnego systemu Windows)** lub **DirectX 12** dla systemu Windows 10.
- [Przykład UAP Direct3D 12](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla systemu Windows 10.
::: moniker-end

Przed przejściem do programu upewnij się, że możesz skompilować i uruchomić aplikację. Wybierz pozycję **Kompiluj**  >  **kompilację rozwiązania** , aby upewnić się, że kompiluje się bez błędów. Następnie wybierz **Debuguj**  >  **Uruchom bez debugowania** (**Ctrl + F5**), aby upewnić się, że działa poprawnie. W zależności od testowanej maszyny za pomocą narzędzia może być konieczne dostosowanie platformy i celu debugowania dla przykładu. Na przykład aby przeprowadzić test względem platformy x64 na maszynie hosta programu Visual Studio, wybierz pozycję **x64** jako platformę rozwiązania i **maszynę lokalną** jako miejsce docelowe debugowania. 

### <a name="2---start-a-graphics-diagnostics-session"></a>2 — Uruchamianie sesji Diagnostyka grafiki
 Teraz wszystko jest gotowe do rozpoczęcia pierwszej sesji diagnostyki grafiki. W programie Visual Studio w menu głównym wybierz kolejno opcje **Debuguj, grafika, Rozpocznij debugowanie grafiki**lub po prostu naciśnij klawisze **Alt + F5**. Spowoduje to uruchomienie aplikacji w obszarze Diagnostyka grafiki i wyświetlenie okien sesji diagnostyki w programie Visual Studio.

> [!IMPORTANT]
> Jeśli uruchamiasz aplikację w systemie Windows 10 i nie zainstalowano jeszcze opcjonalnych narzędzi graficznych, zostanie wyświetlony monit o to, aby to zrobić teraz. Należy ją zainstalować przed użyciem Diagnostyka grafiki w systemie Windows 10.

### <a name="3---capture-frames"></a>3 — Przechwyć ramki
 Możesz teraz przechwycić ramki zaraz po uruchomieniu aplikacji.

#### <a name="to-capture-single-frames"></a>Aby przechwycić pojedyncze ramki

- W programie Visual Studio wybierz przycisk **przechwytywania ramki** z paska narzędzi grafiki lub okna sesji diagnostyki. Lub, jeśli aplikacja ma fokus, po prostu naciśnij klawisz **Print Screen** na klawiaturze.

#### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencję ramek

- W programie Visual Studio, w oknie sesji diagnostycznej, ustaw **ramki do przechwycenia** do liczby ramek, które mają być przechwytywane w sekwencji, a następnie Przechwyć sekwencję przy użyciu dowolnej metody opisanej powyżej do przechwytywania pojedynczych ramek.

   Aby ponownie przechwycić pojedyncze klatki, ustaw **ramki do przechwycenia** na *1*.

  Po zakończeniu przechwytywania ramek wystarczy zamknąć aplikację lub wybrać przycisk **Zatrzymaj** na pasku narzędzi grafiki lub oknie sesji diagnostycznej.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 — badanie przechwyconych ramek w analizatorze grafiki
 Teraz możesz już przechwycić przechwycone ramki. Aby rozpocząć analizowanie ramki, wybierz numer ramki ramki, którą chcesz przeanalizować z okna sesji diagnostycznej. Spowoduje to otwarcie ramki w **analizatorze grafiki**, w której można użyć narzędzi Diagnostyka grafiki, aby sprawdzić, w jaki sposób aplikacja korzysta z Direct3D do śledzenia problemów z renderowaniem, lub użyć narzędzia do **analizy klatek** , aby zrozumieć jego wydajność.

 Jeśli wybrano niewłaściwą ramkę z okna sesji diagnostycznej lub chcesz przejrzeć inną ramkę, możesz wybrać nową klatkę z analizatora grafiki. Na karcie **obiekt docelowy renderowania** okna dziennik grafiki w obszarze obraz elementu docelowego renderowania rozwiń **listę ramka** , a następnie wybierz inną ramkę do sprawdzenia.

 Aby dowiedzieć się więcej o tym, jak używać narzędzi Analizator grafiki, zobacz [przykłady](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Zobacz też
- [Grafika Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)