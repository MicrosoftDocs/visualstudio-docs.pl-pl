---
title: 'Instrukcje: Ograniczanie Instrumentacji do określonych funkcji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8923323a3aed96a9dd441a4a36b2084ffd8197e6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432652"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Instrukcje: Ograniczenie Instrumentacji do określonych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ograniczyć Instrumentacji i gromadzenia danych do co najmniej jedną funkcję, ustawiając opcje w **zaawansowane** strony **sesji wydajności** ani kierowania stron właściwości binarnych:  
  
- Jeśli określisz funkcje na stronie właściwości sesji wydajności, tylko te funkcje są instrumentowane w instrumentowanych danych binarnych na sesji.  
  
- Jeśli określisz funkcje na stronie właściwości obiektu docelowego binarne tylko funkcje, które są w tym, że są instrumentowane określonego pliku binarnego. Funkcje w innych plików binarnych wydajności działają w zwykły sposób.  
  
  Ograniczenie zbierania danych w ten sposób jest obsługiwana tylko wtedy, gdy metoda profilowania Instrumentacja jest zaznaczone.  
  
> [!NOTE]
> Można również użyć **zaawansowane** strony **sesji wydajności** strony właściwości można ustawić inne opcje, które są dostępne dla narzędzi profilowania [VSInstr](../profiling/vsinstr.md) wiersza polecenia Narzędzie do Instrumentacji.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Ograniczenie Instrumentacji do określonych funkcji w ramach sesji wydajności  
  
1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji, a następnie kliknij przycisk **właściwości**.  
  
    **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
2. Na **stron właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
3. W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni o wpisanie nazwy funkcji, które mają być Instrumentacji:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` jest to nazwa przestrzeni nazw i funkcji. Ma on format `Namespace` **::**`FunctionName`. Użyj średnika do rozdzielenia wielu funkcji. Gwiazdka (\*) do określenia co najmniej jeden znak symbolu wieloznacznego. Na przykład **/ include: MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.  
  
   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnym Profiling Tools (zazwyczaj tools\performance Tools katalogu w obszarze [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] katalog instalacyjny), a następnie wpisz **vsinstr / DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Ograniczenie Instrumentacji do określonych funkcji w pliku binarnym  
  
1. W **Eksplorator wydajności**, zlokalizuj nazwa pliku binarnego w **cele** węzła sesji wydajności.  
  
2. Kliknij prawym przyciskiem myszy nazwa pliku binarnego, a następnie kliknij przycisk **właściwości**.  
  
    **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
3. Na **stron właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
4. W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni o wpisanie nazwy funkcji, które mają być Instrumentacji:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` jest to nazwa przestrzeni nazw i funkcji. Ma on format `Namespace` **::**`FunctionName`. Użyj średnika do rozdzielenia wielu funkcji. Gwiazdka (\*) do określenia co najmniej jeden znak symbolu wieloznacznego. Na przykład **/ include: MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.  
  
   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnym Profiling Tools (zazwyczaj tools\performance Tools katalogu w obszarze [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] katalog instalacyjny), a następnie wpisz **vsinstr / DumpFuncs**  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: Ograniczenie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Instrukcje: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)
