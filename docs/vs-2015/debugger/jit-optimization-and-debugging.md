---
title: Optymalizacja i debugowanie JIT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690536"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania aplikacji zarządzanej program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Domyślnie pomija optymalizację kodu just-in-Time (JIT). Pomijanie optymalizacji JIT oznacza debugowanie niezoptymalizowanego kodu. Kod działa wolniej, ponieważ nie jest zoptymalizowany, ale środowisko debugowania jest znacznie bardziej szczegółowe. Debugowanie zoptymalizowanego kodu jest trudniejsze i zalecane tylko wtedy, gdy napotkasz usterkę, która występuje w zoptymalizowanym kodzie, ale nie można jej odtworzyć w niezoptymalizowanej wersji.  
  
 Optymalizacja JIT jest kontrolowana [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przez **pomijanie optymalizacji JIT przy ładowaniu modułu** . Tę opcję można znaleźć na stronie **Ogólne** w węźle **debugowanie** w oknie dialogowym **Opcje** .  
  
 Jeśli wyczyścisz opcję **Pomiń optymalizację JIT przy ładowaniu modułu** , można debugować zoptymalizowany kod JIT, ale możliwość debugowania może być ograniczona, ponieważ zoptymalizowany kod nie jest zgodny z kodem źródłowym. W efekcie okna debugera, takie jak **locale** i okno **Autostart** mogą nie wyświetlać tak dużej ilości informacji, jak w przypadku debugowania niezoptymalizowanego kodu.  
  
 Kolejną istotną różnicą jest debugowanie za pomocą Tylko mój kod. W przypadku debugowania przy użyciu Tylko mój kod debuger traktuje zoptymalizowany kod jako niebędący kodem użytkownika, który nie powinien być wyświetlany podczas debugowania. W związku z tym, jeśli debugujesz kod zoptymalizowany pod kątem JIT, prawdopodobnie chcesz wyłączyć Tylko mój kod. Aby uzyskać więcej informacji, zobacz  [ograniczanie do tylko mój kod](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Należy pamiętać, że opcja **Pomiń optymalizację JIT podczas ładowania modułu** pomija optymalizację kodu podczas ładowania modułów. W przypadku dołączenia do procesu, który jest już uruchomiony, może zawierać kod, który jest już załadowany, skompilowany i zoptymalizowany. Opcja **Pomiń optymalizację JIT w przypadku ładowania modułu** nie ma wpływu na taki kod, chociaż wpłynie ona na moduły, które są ładowane po dołączeniu. Ponadto opcja **Pomijaj optymalizację JIT przy ładowaniu modułu** nie ma wpływu na moduły, takie jak WinForms.dll, które są tworzone za pomocą narzędzia Ngen.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Zarządzany proces wykonywania](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
