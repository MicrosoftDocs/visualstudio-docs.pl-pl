---
title: Wprowadzenie do diagnostyki grafiki | Microsoft Docs
description: Przygotuj się do Diagnostyka grafiki po raz pierwszy, a następnie przechwyć ramki z aplikacji Direct3D i zbadaj je w Analizatorze grafiki.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70512b4df3be7f11973af244c336b22c59c90f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387609"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do diagnostyki grafiki w programie Visual Studio
W tej sekcji przygotujesz się do pierwszego Diagnostyka grafiki, a następnie przechwycisz ramki z aplikacji Direct3D i przeanalizujemy je w Analizatorze grafiki.

## <a name="requirements"></a>Wymagania
 Aby używać Diagnostyka grafiki w Visual Studio, należy użyć Visual Studio Enterprise, Visual Studio Professional lub Visual Studio Community.  Inne wersje, w tym Visual Studio Code, nie zawierają tej funkcji.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 wymagań wstępnych
 Opcjonalna funkcja *narzędzi graficznych systemu* Windows zapewnia infrastrukturę przechwytywania i odtwarzania wymaganą przez Diagnostyka grafiki na Windows 10.

 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [Instalowanie narzędzi graficznych dla Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalowanie narzędzi graficznych dla Windows 10
 W Windows 10 infrastruktury Diagnostyka grafiki jest dostępna opcjonalna funkcja systemu Windows o nazwie *Narzędzia graficzne.* Ta funkcja jest wymagana do przechwytywania i odtwarzania informacji graficznych na platformie Windows 10 niezależnie od tego, czy przechwytywana aplikacja dotyczy poprzedniej wersji systemu Windows, czy używanej wersji direct3D. Możesz zainstalować funkcję Narzędzia grafiki z wyprzedzeniem. W przeciwnym razie zostanie ona zainstalowana na żądanie przy pierwszym uruchomieniu sesji Diagnostyka grafiki z Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzia graphics tools for Windows 10

1. W polu Wyszukaj wpisz **Aplikacje i funkcje,** a następnie otwórz ustawienia **& funkcji.**

2. Po prawej stronie ustawień Funkcje aplikacji & wybierz pozycję **Funkcje** opcjonalne **(w** obszarze Aplikacje **& funkcje).**

   Zostaną **wyświetlone ustawienia Funkcje** opcjonalne.

3. W **ustawieniach Funkcje opcjonalne** wybierz pozycję **Dodaj funkcję.** Zostanie wyświetlona lista opcjonalnych funkcji, które można zainstalować.

4. Wybierz **pozycję Narzędzia graficzne** z listy funkcji, a następnie wybierz pozycję **Zainstaluj**.

   Funkcja narzędzi graficznych jest również instalowana automatycznie podczas instalowania zestawu WINDOWS 10 SDK.

> [!TIP]
> Opcjonalna funkcja narzędzi graficznych programu Windows 10 zapewnia uproszczone funkcje przechwytywania i odtwarzania, takie jak program do przechwytywania wiersza polecenia **dxcap.exe,** które mogą być używane w scenariuszach obsługi, testowania i diagnostyki na maszynach, na których nie są zainstalowane narzędzia deweloperskie. Aby uzyskać więcej informacji, zobacz [temat Narzędzie do przechwytywania wiersza](command-line-capture-tool.md) polecenia.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie Diagnostyka grafiki po raz pierwszy
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz rozpocząć korzystanie z Diagnostyka grafiki. Wystarczy wykonać poniższe czynności.

### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji Direct3D

Jeśli masz już własną aplikację Direct3D, która umożliwia eksplorowanie Diagnostyka grafiki, świetnie! W przeciwnym razie użyj jednej z następujących czynności:

::: moniker range=">=vs-2019"
Pobierz przykład z [przykładowej gry Direct3D.](/samples/microsoft/windows-universal-samples/simple3dgamedx/)
::: moniker-end
::: moniker range="vs-2017"
- Szablony **projektów aplikacji DirectX 11 (uniwersalny** system Windows) lub Aplikacji **DirectX 12 (uniwersalny system Windows)** dla Windows 10.
- [Przykład direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla Windows 10.
::: moniker-end

Przed przejściem upewnij się, że możesz skompilować i uruchomić aplikację. Wybierz **pozycję Build** Build Solution (Skompilowanie rozwiązania  >   kompilacji), aby upewnić się, że jest ono kompilowane bez błędów. Następnie wybierz pozycję **Rozpocznij**  >  **debugowanie bez debugowania** **(Ctrl + F5),** aby upewnić się, że działa poprawnie. W zależności od maszyny testowej za pomocą narzędzia może być konieczne dostosowanie platformy i celu debugowania dla przykładu. Aby na przykład przetestować platformę x64 na maszynie hosta Visual Studio, wybierz platformę rozwiązania **x64** i maszynę lokalną jako element docelowy debugowania.  

### <a name="2---start-a-graphics-diagnostics-session"></a>2 — Uruchamianie Diagnostyka grafiki sesji
 Teraz możesz rozpocząć pierwszą sesję diagnostyki grafiki. W Visual Studio menu głównym wybierz pozycję **Debuguj, Grafika, Rozpocznij debugowanie** grafiki lub po prostu naciśnij **klawisze Alt+F5.** Powoduje to rozpoczęcie aplikacji w Diagnostyka grafiki i wyświetlenie okien sesji diagnostyki w Visual Studio.

> [!IMPORTANT]
> Jeśli aplikacja jest uruchomiona na komputerze Windows 10 i nie zainstalowano jeszcze opcjonalnej funkcji Narzędzia grafiki, zostanie wyświetlony monit o jej wykonanie. Należy go zainstalować, aby można było używać Diagnostyka grafiki na Windows 10.

### <a name="3---capture-frames"></a>3 — Przechwytywanie ramek
 Możesz przechwycić ramki zaraz po uruchamianych aplikacjach.

#### <a name="to-capture-single-frames"></a>Przechwytywanie pojedynczych ramek

- W Visual Studio wybierz przycisk **Przechwyć** ramkę z paska narzędzi Grafiki lub okna sesji diagnostyki. Jeśli aplikacja ma fokus, po prostu naciśnij klawisz **Print Screen** na klawiaturze.

#### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencję ramek

- W Visual Studio oknie sesji diagnostycznej ustaw  pozycję Ramki do przechwycenia na liczbę ramek do przechwycenia kolejno, a następnie przechwyć sekwencję przy użyciu dowolnej z metod opisanych powyżej, aby przechwycić pojedyncze ramki.

   Aby ponownie przechwycić pojedyncze ramki, ustaw **dla ramek wartość** *1*.

  Po wykonaniu przechwytywania ramek wystarczy zamknąć aplikację  lub wybrać przycisk Zatrzymaj na pasku narzędzi Grafiki lub w oknie sesji diagnostycznej.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 — Badanie przechwyconych ramek w analizatorze grafiki
 Teraz możesz przeanalizować przechwycone ramki. Aby rozpocząć analizowanie ramki, wybierz numer ramki, którą chcesz zbadać, z okna sesji diagnostycznej. Spowoduje to otwarcie ramki w Analizatorze grafiki **,** w którym można użyć narzędzi usługi Diagnostyka grafiki, aby sprawdzić, w  jaki sposób aplikacja używa direct3D do śledzenia problemów z renderowaniem, lub użyć narzędzia do analizy ramek w celu zrozumienia jej wydajności.

 Jeśli wybrano nieprawidłową ramkę w oknie sesji diagnostycznej lub chcesz zbadać inną ramkę, możesz wybrać nową ramkę z analizatora grafiki. Na karcie **Render Target (Cel** renderowania) w oknie dziennika grafiki w obszarze renderowanego obrazu docelowego rozwiń listę **ramek,** a następnie wybierz inną ramkę do zbadania.

 Aby dowiedzieć się więcej o tym, jak używać razem narzędzi Analizator grafiki, zobacz [Przykłady](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Zobacz też
- [Grafika Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)