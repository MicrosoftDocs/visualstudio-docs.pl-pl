---
title: Lista stosu wywołań — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 932dbc9e3971598748e462de92280ac7112f8c62
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665119"
---
# <a name="list-call-stack-command"></a>Lista stosu wywołań — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla bieżący stos wywołań.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Opcjonalna. Ustawia bieżącej ramki stosu i nie wyświetla danych wyjściowych.  
  
## <a name="switches"></a>Przełączniki  
 Każdy przełącznik może być wywoływany przy użyciu jego wypełniony formularz lub krótka.  
  
 / Liczba:`number` [i] / c:`number`  
 Opcjonalna. Maksymalna liczba stosy wywołań do wyświetlenia. Wartością domyślną jest nieograniczona.  
  
 /ShowTypes:`yes`&#124;`no` [or] /T:`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane typy parametrów. Wartość domyślna to `yes`.  
  
 /ShowNames:`yes`&#124;`no` [or] /N:`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane nazwy parametrów. Wartość domyślna to `yes`.  
  
 /ShowValues:`yes`&#124;`no` [or] /V:`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane wartości parametrów. Wartość domyślna to `yes`.  
  
 / ShowModule:`yes` &#124; `no` [i] / m:`yes`&#124;`no`  
 Opcjonalna. Określa, czy ma być wyświetlana nazwa modułu. Wartość domyślna to `yes`.  
  
 /ShowLineOffset:`yes`&#124;`no` [or] /#:`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane przesunięcie wiersza. Wartość domyślna to `no`.  
  
 /ShowByteOffset:`yes`&#124;`no` [or] /B:`yes`&#124;`no`  
 Opcjonalna. Określa, czy należy wyświetlać przesunięcie bajtu. Wartość domyślna to `no`.  
  
 / ShowLanguage:`yes` &#124; `no` [i] / l: wyświetlenie`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane w języku. Wartość domyślna to `no`.  
  
 /IncludeCallsAcrossThreads:`yes`&#124;`no` [or] /I:`yes`&#124;`no`  
 Opcjonalna. Określa, czy dołączać wywołania do lub z innych wątków. Wartość domyślna to `no`.  
  
 /ShowExternalCode:`yes`&#124;`no`  
 Opcjonalna. Określa, czy mają być wyświetlane tylko mój kod dla stosu wywołań. Gdy tylko mój kod jest wyłączona, wyświetlany jest cały kod niezwiązany z użytkownikiem. Po włączeniu tylko mój kod niebędący kodem użytkownika jest wyświetlany jako `[external]` w danych wyjściowych stosu wywołań.  
  
 Wątek:`n`  
 Opcjonalna. Przedstawia stos wywołań dla wątku `n`. Jeśli żaden wątek nie zostanie określony, wyświetla stos wywołań dla bieżącego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Zmiany wprowadzone do argumentów lub przełączników dotyczą przyszłych wywołań tego polecenia. Jeśli wydawane Debug.ListCallStackby sam Wyświetla cały stos wywołań. Jeśli na przykład określić indeks  
  
```  
Debug.ListCallStack 2  
```  
  
 Bieżąca ramka stosu przybiera wartość do tej ramki (w tym przypadku drugiej ramki).  
  
 Możesz również zapisywać dane tego polecenia, używając jego wstępnie zdefiniowanych aliasów kb. Na przykład można wprowadzić  
  
```  
kb 2  
```  
  
 można ustawić bieżącej ramki stosu do drugiego ramki.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dezasemblacji — polecenie](../../ide/reference/list-disassembly-command.md)   
 [Lista wątków — polecenie](../../ide/reference/list-threads-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
