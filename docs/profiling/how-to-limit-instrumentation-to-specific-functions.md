---
title: 'Instrukcje: Ograniczanie Instrumentacji do określonych funkcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e145a50c3fdb643affb67989ae11346bf7e30f9
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592862"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Instrukcje: Ograniczanie instrumentacji do określonych funkcji
Można ograniczyć Instrumentacji i gromadzenia danych do co najmniej jedną funkcję, ustawiając opcje w **zaawansowane** strony **sesji wydajności** ani kierowania stron właściwości binarnych:  
  
- Jeśli określisz funkcje na stronie właściwości sesji wydajności, tylko te funkcje są instrumentowane w instrumentowanych danych binarnych na sesji.  
  
- Jeśli określisz funkcje na stronie właściwości obiektu docelowego binarne tylko funkcje, które są w tym, że są instrumentowane określonego pliku binarnego. Funkcje w innych plików binarnych wydajności działają w zwykły sposób.  
  
  Ograniczenie zbierania danych w ten sposób jest obsługiwana tylko wtedy, gdy metoda profilowania Instrumentacja jest zaznaczone.  
  
> [!NOTE]
>  Można również użyć **zaawansowane** strony **sesji wydajności** strony właściwości można ustawić inne opcje, które są dostępne dla narzędzi profilowania [VSInstr](../profiling/vsinstr.md) wiersza polecenia Narzędzie do Instrumentacji.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Ograniczenie Instrumentacji do określonych funkcji w ramach sesji wydajności  
  
1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji, a następnie kliknij przycisk **właściwości**.  
  
    **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
2. Na **stron właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
3. W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni o wpisanie nazwy funkcji, które mają być Instrumentacji:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` jest to nazwa przestrzeni nazw i funkcji. Ma on format `Namespace` **::**`FunctionName`. Użyj średnika do rozdzielenia wielu funkcji. Gwiazdka (\*) do określenia co najmniej jeden znak symbolu wieloznacznego. Na przykład **/ include: MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.  
  
   > [!NOTE]
   >  Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnym Profiling Tools (zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), a następnie wpisz **vsinstr /DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Ograniczenie Instrumentacji do określonych funkcji w pliku binarnym  
  
1. W **Eksplorator wydajności**, zlokalizuj nazwa pliku binarnego w **cele** węzła sesji wydajności.  
  
2. Kliknij prawym przyciskiem myszy nazwa pliku binarnego, a następnie kliknij przycisk **właściwości**.  
  
    **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
3. Na **stron właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
4. W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni o wpisanie nazwy funkcji, które mają być Instrumentacji:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` jest to nazwa przestrzeni nazw i funkcji. Ma on format `Namespace` **::**`FunctionName`. Użyj średnika do rozdzielenia wielu funkcji. Gwiazdka (\*) do określenia co najmniej jeden znak symbolu wieloznacznego. Na przykład **/ include: MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.  
  
   > [!NOTE]
   >  Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnym Profiling Tools (zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), a następnie wpisz **vsinstr /DumpFuncs**  
  
## <a name="see-also"></a>Zobacz także  
 [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: Ograniczenie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Instrukcje: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)