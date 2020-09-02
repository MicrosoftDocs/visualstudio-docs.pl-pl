---
title: 'Instrukcje: debugowanie zoptymalizowanego kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ce036d420293e8a75bec1b2cac9f9ee8f8fcd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675613"
---
# <a name="how-to-debug-optimized-code"></a>Porady: debugowanie zoptymalizowanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
> Opcja kompilatora [/zo (rozszerzanie zoptymalizowanego debugowania)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)(wprowadzona w Visual Studio Update 3) generuje bogatsze informacje debugowania dla zoptymalizowanego kodu (projekty, które nie zostały skompilowane przy użyciu opcji kompilatora **/od** ). Zobacz [/O opcje (Optymalizuj kod)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). Obejmuje to ulepszoną obsługę debugowania zmiennych lokalnych i funkcji w wierszu.  
>   
> Polecenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md) jest wyłączone, gdy jest używana opcja **/zo** ocompiler.  
  
 Gdy kompilator optymalizuje kod, zmienia położenie i Reorganizuje instrukcje. Powoduje to bardziej wydajne skompilowane kod. Ze względu na to ponowne rozmieszczenie debuger nie zawsze identyfikuje kod źródłowy, który odpowiada zestawowi instrukcji.  
  
 Optymalizacja może mieć wpływ na:  
  
- Zmienne lokalne, które mogą zostać usunięte przez optymalizator lub przeniesione do lokalizacji debuger nie rozpoznaje.  
  
- Położenie wewnątrz funkcji, które są zmieniane, gdy optymalizator Scala bloki kodu.  
  
- Nazwy funkcji dla ramek na stosie wywołań, które mogą być nieprawidłowe, jeśli optymalizator Scala dwie funkcje.  
  
  Ramki widoczne na stosie wywołań są prawie zawsze poprawiane, jednak przy założeniu, że masz symbole dla wszystkich ramek. Ramki na stosie wywołań będą niewłaściwe w przypadku uszkodzenia stosu, jeśli masz funkcje w języku zestawu lub jeśli istnieją ramki systemu operacyjnego bez pasujących symboli w stosie wywołań.  
  
  Zmienne globalne i statyczne są zawsze wyświetlane poprawnie. Tak więc jest układ struktury. Jeśli masz wskaźnik do struktury i wartość wskaźnika jest poprawna, Każda zmienna elementu członkowskiego struktury będzie zawierać poprawną wartość.  
  
  Ze względu na te ograniczenia należy debugować przy użyciu niezoptymalizowanej wersji programu, jeśli jest to możliwe. Domyślnie optymalizacja jest wyłączona w konfiguracji debugowania programu Visual C++ i włączona w konfiguracji wydania.  
  
  Usterka może jednak wystąpić tylko w zoptymalizowanej wersji programu. W takim przypadku należy debugować zoptymalizowany kod.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Aby włączyć optymalizację w konfiguracji kompilacji debugowania  
  
1. Podczas tworzenia nowego projektu, wybierz `Win32 Debug` element docelowy. Użyj `Win32``Debug` elementu docelowego do momentu, gdy program jest w pełni debugowany i wszystko jest gotowe do skompilowania `Win32 Release` celu. Kompilator nie optymalizuje `Win32 Debug` elementu docelowego.  
  
2. Wybierz projekt w Eksplorator rozwiązań.  
  
3. W menu **Widok** kliknij polecenie **strony właściwości**.  
  
4. Na **stronie właściwości** okno dialogowe, upewnij się, że `Debug` jest zaznaczone na liście rozwijanej **Konfiguracja** .  
  
5. W widoku folderu po lewej stronie Wybierz folder **C/C++** .  
  
6. W folderze **C++** wybierz opcję `Optimization` .  
  
7. Na liście właściwości po prawej stronie Znajdź `Optimization` . Obok tego ustawienia prawdopodobnie widnieje `Disabled (` [/od](https://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5) `)` . Wybierz jedną z innych opcji ( `Minimum Size``(` [/O1](https://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2) `)` , `Maximum Speed``(` [/O2](https://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2) `)` , `Full Optimization``(` [/OX](https://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760) `)` lub `Custom` ).  
  
8. W przypadku wybrania `Custom` opcji dla `Optimization` , można teraz ustawić opcje dla każdej z pozostałych właściwości wyświetlanych na liście właściwości.  
  
9. Wybierz właściwości konfiguracji, C/C++, węzeł wiersza polecenia na stronie właściwości projektu i Dodaj `(` [/zo](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` do pola tekstowego **Opcje dodatkowe** .  
  
    > [!WARNING]
    > `/Zo` wymaga Visual Studio 2013 Update 3 lub nowszą wersję.  
    >   
    >  Dodanie `/Zo` spowoduje wyłączenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md).  
  
   Podczas debugowania zoptymalizowanego kodu Użyj okna **demontażu** , aby zobaczyć, jakie instrukcje są w rzeczywistości tworzone i wykonywane. Po ustawieniu punktów przerwania należy się dowiedzieć, że punkt przerwania może zostać przesunięty razem z instrukcją. Rozważmy na przykład następujący kod:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Załóżmy, że ustawisz punkt przerwania w tym wierszu. Może oczekiwać, że punkt przerwania zostanie osiągnięty 10 razy, ale jeśli kod jest zoptymalizowany, punkt przerwania zostanie trafiony tylko raz. Oznacza to, że pierwsza instrukcja ustawia wartość `x` na 0. Kompilator rozpoznaje, że tylko raz i przenosi go z pętli. Punkt przerwania jest przenoszony razem z nim. Instrukcje, które porównują i zwiększają, `x` pozostają wewnątrz pętli. Po wyświetleniu okna **demontażu** [Jednostka kroku](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) jest automatycznie ustawiana na instrukcje w celu uzyskania większej kontroli, co jest przydatne w przypadku przechodzenia przez zoptymalizowany kod.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
