---
title: 'Instrukcje: ograniczanie instrumentacji do określonych funkcji | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788035"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Porady: ograniczanie instrumentacji do określonych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ograniczyć instrumentację i zbieranie danych do co najmniej jednej funkcji przez ustawienie opcji na stronie **Zaawansowane** **sesji wydajności** lub docelowej strony właściwości binarnych:  
  
- Jeśli określisz funkcje na stronie właściwości sesji wydajności, tylko te funkcje są Instrumentacją we wszystkich plikach binarnych z instrumentacją sesji.  
  
- Jeśli określisz funkcje na stronie właściwości w docelowym pliku binarnym, tylko te funkcje, które znajdują się w tym konkretnym pliku binarnym, są Instrumentacją. Funkcje w innych plikach binarnych wydajności są przystosowane w zwykły sposób.  
  
  Ograniczanie zbierania danych w ten sposób jest obsługiwane tylko wtedy, gdy wybrano metodę profilowania Instrumentacji.  
  
> [!NOTE]
> Możesz również użyć strony **Zaawansowane** strony właściwości **sesji wydajności** , aby ustawić inne opcje dostępne dla narzędzia instrumentacja wiersza polecenia narzędzia profilowania [VSInstr](../profiling/vsinstr.md) .  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Aby ograniczyć instrumentację do określonych funkcji w sesji wydajności  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji, a następnie kliknij polecenie **Właściwości**.  
  
    Wyświetli się okno dialogowe **Strony właściwości**.  
  
2. Na **stronie właściwości** okno dialogowe, kliknij przycisk **Zaawansowane**.  
  
3. W polu tekstowym **dodatkowe opcje Instrumentacji** wpisz nazwę funkcji, które chcesz przystosować, używając następującej składni:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
    `FuncSpec` jest przestrzenią nazw i nazwą funkcji. Ma format `Namespace` **::** `FunctionName` . Użyj średnika do rozdzielenia wielu funkcji. Użyj gwiazdki ( \* ), aby określić symbol wieloznaczny dla co najmniej jednego znaku. Na przykład **/include: MyNS:: \\ *** określa wszystkie funkcje w przestrzeni nazw myNs.  
  
   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacji narzędzia profilowania (zazwyczaj w katalogu \Team Tools\Performance Tools w [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] katalogu instalacji), a następnie wpisz **VSInstr/DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Aby ograniczyć instrumentację do określonych funkcji w pliku binarnym  
  
1. W **Eksplorator wydajności**Zlokalizuj nazwę binarną w węźle **targets** sesji wydajności.  
  
2. Kliknij prawym przyciskiem myszy nazwę binarną, a następnie kliknij polecenie **Właściwości**.  
  
    Wyświetli się okno dialogowe **Strony właściwości**.  
  
3. Na **stronie właściwości** okno dialogowe, kliknij przycisk **Zaawansowane**.  
  
4. W polu tekstowym **dodatkowe opcje Instrumentacji** wpisz nazwę funkcji, które chcesz przystosować, używając następującej składni:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
    `FuncSpec` jest przestrzenią nazw i nazwą funkcji. Ma format `Namespace` **::** `FunctionName` . Użyj średnika do rozdzielenia wielu funkcji. Użyj gwiazdki ( \* ), aby określić symbol wieloznaczny dla co najmniej jednego znaku. Na przykład **/include: MyNS:: \\ *** określa wszystkie funkcje w przestrzeni nazw myNs.  
  
   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacji narzędzia profilowania (zazwyczaj w katalogu \Team Tools\Performance Tools w [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] katalogu instalacji), a następnie wpisz **VSInstr/DumpFuncs**  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Instrukcje: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)
