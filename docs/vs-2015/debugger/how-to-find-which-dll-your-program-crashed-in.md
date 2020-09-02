---
title: 'Instrukcje: Znajdowanie biblioteki DLL, w której nastąpiła awaria programu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703631"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Porady: odnajdywanie biblioteki DLL, w której nastąpiła awaria programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Jeśli aplikacja ulegnie awarii podczas wywołania do systemowej biblioteki DLL lub kodu innej osoby, należy dowiedzieć się, która Biblioteka DLL była aktywna w przypadku wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza własnym programem, można zidentyfikować lokalizację przy użyciu okna **moduły** .  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Aby sprawdzić, w którym miejscu wystąpił awaria przy użyciu okna moduły  
  
1. Zanotuj adres, na którym wystąpiła awaria.  
  
2. W menu **Debuguj** wybierz pozycję **Windows**, a następnie kliknij opcję **moduły**.  
  
3. W oknie **moduły** Znajdź kolumnę **adres** . Może być konieczne użycie paska przewijania, aby go zobaczyć.  
  
4. Kliknij przycisk **adresu** w górnej części kolumny, aby posortować biblioteki DLL według adresu.  
  
5. Zeskanuj posortowaną listę, aby znaleźć bibliotekę DLL, której zakres adresów zawiera lokalizację awarii.  
  
6. Przejrzyj kolumny **Nazwa** i **ścieżka** , aby wyświetlić nazwę i ścieżkę biblioteki DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: debugowanie natywnych bibliotek DLL](../debugger/how-to-debug-native-dlls.md)   
 [Instrukcje: korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)
