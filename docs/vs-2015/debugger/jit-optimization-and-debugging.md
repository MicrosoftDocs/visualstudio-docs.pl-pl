---
title: JIT Optymalizacja i debugowanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b4a0cf53dcc9870b5d0c93d2fcaaf2d942fd9959
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767941"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania aplikacji zarządzanych, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomija optymalizację kodu just-in-time (JIT) domyślnie. Pomijanie optymalizacji JIT oznacza, że debugujesz kod niezoptymalizowany. Kod działa nieco wolniej, ponieważ nie jest zoptymalizowana, ale środowisko debugowania jest dużo większe. Debugowanie zoptymalizowanego kodu jest trudniejsze i zalecane tylko wtedy, jeśli napotkasz usterkę, która występuje w zoptymalizowanym kodzie, ale nie może być odtworzony w wersji niezoptymalizowanej.  
  
 Optymalizacja JIT jest kontrolowana w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przez **Pomijaj optymalizację JIT podczas ładowania modułu** opcji. Tej opcji można znaleźć na **ogólne** strony w obszarze **debugowanie** w węźle **opcje** okno dialogowe.  
  
 Jeśli wyczyścisz **Pomijaj optymalizację JIT podczas ładowania modułu** opcji można debugować zoptymalizowany kod JIT, ale może być ograniczona możliwość debugowania, ponieważ zoptymalizowany kod nie pasuje do kodu źródłowego. W rezultacie debugera, takie jak **lokalne** i **Autos** okna mogą nie wyświetlać tylu informacji tak samo jak Gdybyś debugował kod niezoptymalizowany.  
  
 Inna ważna różnica dotyczy debugowania przy użyciu tylko mój kod. Jeśli debugujesz z funkcją tylko mój kod, debuger uważa zoptymalizowany kod za kod niezwiązany z użytkownikiem, który nie powinien być wyświetlany podczas debugowania. W związku z tym Jeśli debugujesz zoptymalizowany kod JIT, prawdopodobnie chcesz wyłączyć opcję tylko mój kod. Aby uzyskać więcej informacji, zobacz [Ogranicz przechodzenie krok po kroku, aby tylko mój kod](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Należy pamiętać, że **Pomijaj optymalizację JIT podczas ładowania modułu** opcji powoduje pominięcie optymalizacji kodu podczas załadowania. Jeśli dołączysz do procesu, który jest już uruchomiony, może zawierać kod, który jest już załadowany, skompilowany JIT i zoptymalizowane. **Pomijaj optymalizację JIT podczas ładowania modułu** opcja nie ma wpływu na taki kod, chociaż ma wpływ na moduły, które są ładowane po dołączeniu. Ponadto **Pomijaj optymalizację JIT podczas ładowania modułu** opcja wpływa na moduły, takie jak WinForms.dll, które są tworzone za pomocą narzędzia NGEN.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces zarządzanego wykonania](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
