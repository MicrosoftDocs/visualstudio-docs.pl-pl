---
title: Przechwytywanie informacji graficznych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: 44
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b78492ccd5c2666da5ffc503cdf126842431478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702554"
---
# <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przechwyć informacje graficzne z aplikacji Direct3D, aby móc używać analizator grafiki programu Visual Studio do diagnozowania problemów z renderowaniem i problemów z wydajnością.  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Przechwytywanie informacji graficznych jest procesem dwuetapowym. Po pierwsze, uruchom aplikację w obszarze Diagnostyka grafiki, a następnie określ jedną lub więcej ramek, z których zostaną przechwycone szczegółowe informacje.  
  
#### <a name="to-run-your-app-under-graphics-diagnostics"></a>Aby uruchomić aplikację w obszarze Diagnostyka grafiki  
  
- Na pasku menu wybierz kolejno opcje **Debuguj**, **grafika**i **Uruchom diagnostykę**. (Klawiatura: naciśnij klawisze Alt+F5)  
  
- Na pasku narzędzi **grafiki** wybierz przycisk **Rozpocznij diagnostykę** .  
  
  Gdy aplikacja jest uruchomiona w ramach diagnostyki grafiki, pewne rodzaje informacji graficznych są cały czas przechwytywane; obejmuje to konfigurację urządzenia, tworzenie łańcucha wymiany elementów, tworzenie grafiki, obiektów i zasobów oraz inne ważne wydarzenia, które wpływają na więcej niż jedną klatkę. W tym samym czasie można przechwycić szczegółowe informacje na temat konkretnych klatek. Dotyczy to wywołania rysowań i wysyłań cieniowania obliczenia, wraz z obiektami i zasobami Direct3D, które je obsługują.  
  
#### <a name="to-capture-a-frame"></a>Aby przechwycić ramkę  
  
- W programie Visual Studio na pasku narzędzi **grafika** wybierz ikonę **przechwytywania** ![grafiki](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")przycisku przechwytywania.  
  
- Na klawiaturze naciśnij klawisz Print Screen.  
  
  > [!NOTE]
  > Gdy aplikacja działa w **Diagnostyka grafiki**, można użyć klawisza Print Screen tylko do przechwytywania ramki informacji graficznych. nie wykonuje swojej zwykłej funkcji. To pozostaje, dopóki nie zatrzymasz przechwytywania informacji graficznych — zwykle przez zatrzymanie debugowania lub normalne wyjście z aplikacji — nawet wtedy, gdy fokus jest na innej aplikacji.  
  
- W interfejsie przechwytywania programu Visual Studio wybierz przycisk **przechwytywania ramki** znajdujący się powyżej osi czasu **sesji diagnostycznej** lub wybierz przycisk dużej **ramki przechwytywania** znajdującego się poniżej **ramek na sekundę** torach-Lane i po prawej stronie wszystkich wcześniej przechwyconych ramek. Oba przyciski zostały wyróżnione na poniższej ilustracji.  
  
   ![Przechwyć ramki przy użyciu narzędzia użycie procesora GPU.](../debugger/media/pix-gpu-usage-tool-capture-frame.png "pix_gpu_usage_tool_capture_frame")  
  
   Aby przejrzeć przechwycone ramki, uruchom **Analizator grafiki programu Visual Studio** , postępując zgodnie z **ramką...** łącze powyżej miniatur obrazu lub przez dwukrotne kliknięcie miniatury.  
  
  Tylko całe ramki mogą być przechwytywane, więc po zainicjowaniu przechwytywania tak naprawdę to informacje grafiki z następnej ramki są rejestrowane. Zapisywanie rozpoczyna się natychmiast po zaprezentowaniu klatki, w której rozpocząłeś przechwytywanie, i kończy się po zaprezentowaniu przechwyconej klatki. Możesz przechwycić tyle klatek, ile chcesz, gdy aplikacja jest uruchomiona w ramach diagnostyki grafiki. Jeśli nie przechwycisz żadnej ramki, dziennik grafiki jest odrzucany.  
  
  Podczas przechwytywania ramek program Visual Studio Wyświetla okno sesji diagnostyki (. diagsession). Po zamknięciu tego okna, zatrzymaniu debugowania lub zamknięciu aplikacji nie można przechwycić więcej ramek do tego dziennika. Aby przechwycić więcej informacji graficznych, należy uruchomić aplikację ponownie w Diagnostyka grafiki, aby rozpocząć nową sesję diagnostyki.  
  
### <a name="graphics-diagnostics-capture-options"></a>Opcje przechwytywania Diagnostyka grafiki  
 Można skonfigurować funkcję przechwytywania, aby zbierać stosy wywołań dla wszystkich zdarzeń graficznych lub ograniczonego podzestawu, wyłączać HUD przechwytywania i włączać lub wyłączać tryb zgodności przechwytywania.  
  
##### <a name="to-configure-graphics-diagnostics-capture-options"></a>Aby skonfigurować opcje przechwytywania Diagnostyka grafiki  
  
1. Na pasku menu wybierz narzędzia, opcje. Zostanie wyświetlone okno dialogowe Opcje.  
  
2. Na liście Kategoria opcji po lewej stronie wybierz pozycję Diagnostyka grafiki, a następnie skonfiguruj odpowiednie opcje Diagnostyka grafiki.  
  
     **Zbieraj stosy wywołań podczas przechwytywania (powoduje wolniejsze przechwytywanie)**  
     Zaznacz to pole, aby zebrać stosy wywołań. Domyślnie stosy wywołań nie są zbierane. Aby przechwytywać stosy wywołań, upewnij się, że **stosy wywołań podczas przechwytywania (powoduje, że pole wyboru Przechwyć wolniej** jest ustawione na wartość Włącz zbieranie, a następnie ustaw opcję **dla opcji rysowania, wysyłania, prezentowania i wydajności** (domyślnie), aby zebrać tylko najważniejsze stosy wywołań lub opcję **dla wszystkiego** , aby zebrać wszystkie stosy wywołań. Aby później przerwać zbieranie stosów wywołań, wyczyść pole wyboru **Zbieraj stosy wywołań podczas przechwytywania (powoduje wolniejsze przechwytywanie** ).  
  
     **Wyłącz HUD gry podczas przechwytywania**  
     Zaznacz to pole, aby wyłączyć nakładkę HUD, która jest zwykle wyświetlana w aplikacji działającej w ramach diagnostyki grafiki. Usuń zaznaczenie tego pola, aby wyświetlić nakładkę HUD.  
  
     **Przechwyć w trybie zgodności**  
     Zaznacz to pole, aby przechwycić informacje graficzne w trybie zgodności. Ustawieniem domyślnym jest przechwytywanie w trybie zgodności. W obszarze Tryb zgodności Direct3D nie będzie zgłaszać, że procesor GPU obsługuje wszelkie dodatkowe funkcje wykraczające poza te zdefiniowane na poziomie podstawowej funkcji. Zapobiega to przechwyceniu aplikacji przy użyciu rozszerzeń specyficznych dla sprzętu procesora GPU przechwyconych w systemie i zapewnia, że dziennik grafiki można odtworzyć przy użyciu dowolnego procesora GPU, który obsługuje ten sam lub wyższy poziom funkcji. Usuń zaznaczenie tego pola, aby wyłączyć tryb zgodności; Dzienniki przechwycone z trybem zgodności nie będą odtwarzane na żadnym procesorze GPU, który nie obsługuje tych samych dodatkowych funkcji, które były używane przez aplikację podczas przechwytywania.  
  
     **Zatrzymaj przechwytywanie, jeśli wystąpią błędy warstw zestawu SDK**  
     Zaznacz to pole, aby zatrzymać przechwytywanie natychmiast w przypadku napotkania błędów.  
  
## <a name="capturing-graphics-information-remotely"></a>Zdalne przechwytywanie informacji graficznych  
 Informacje graficzne mogą być przechwytywane z aplikacji, która jest uruchomiona na komputerze lokalnym lub na zdalnym komputerze lub urządzeniu. Zdalne przechwytywanie jest obsługiwane w przypadku [!INCLUDE[winblue_client_2](../includes/winblue-client-2-md.md)] maszyn i [!INCLUDE[winblue_winrt_2](../includes/winblue-winrt-2-md.md)] urządzeń. Aby przechwytywać informacje graficzne z aplikacji, która jest uruchomiona zdalnie, skonfiguruj projekt dla zdalnego debugowania, a następnie uruchom aplikację w obszarze Diagnostyka grafiki zgodnie z wcześniejszym opisem. Aplikacja jest uruchamiana na komputerze zdalnym, a przechwycone informacje graficzne są rejestrowane na komputerze deweloperskim.  
  
 Konfiguracja projektu dla zdalnego debugowania zależy od rodzaju aplikacji, którą projektujesz, i języka programowania, którego używasz. Aby uzyskać informacje na temat sposobu konfigurowania zdalnego debugowania dla aplikacji ze sklepu Windows, zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md). Aby uzyskać informacje o sposobie konfigurowania zdalnego debugowania dla aplikacji klasycznych systemu Windows, zobacz [Konfigurowanie zdalnego debugowania dla projektu programu Visual Studio](https://msdn.microsoft.com/library/ec332dc4-400a-498b-a0e6-c8dcf10fef8a).  
  
 Później można użyć zdalnego komputera lub urządzenia do odtwarzania informacji graficznych, bez względu na to, gdzie informacje zostały przechwycone. Aby uzyskać więcej informacji, zobacz [How to: Change a Diagnostyka grafiki playback Machine](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Przechwytywanie informacji graficznych z wiersza polecenia  
 Informacje o grafice mogą być przechwytywane z aplikacji za pomocą narzędzia wiersza polecenia. To narzędzie, DXCap.exe, umożliwia szybkie przechwytywanie i odtwarzanie informacji graficznych bez użycia programu Visual Studio lub funkcji przechwytywania programowego. W szczególności można użyć DXCap.exe do automatyzacji lub w środowisku testowym. Aby uzyskać więcej informacji na temat DXCap.exe, zobacz [Narzędzie do przechwytywania wiersza polecenia](../debugger/command-line-capture-tool.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Przechwytywanie informacji graficznych](../debugger/walkthrough-capturing-graphics-information.md)
