---
title: 'Instrukcje: Odnajdywanie DLL, która nastąpiła awaria programu | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 33e59a2109e408a290ab8b05a5fd8208c7bd1853
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438257"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Instrukcje: Odnajdywanie DLL, która nastąpiła awaria programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Jeśli aplikacja ulegnie awarii podczas wywoływania biblioteki DLL systemu lub innej osoby kodu, musisz znaleźć się, które biblioteki DLL była aktywna podczas wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza własny program, można zidentyfikować lokalizację za pomocą **modułów** okna.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Aby dowiedzieć się, w przypadku, gdy awaria wystąpił podczas korzystania z okna modułów  
  
1. Zanotuj adres, w których wystąpiła awaria.  
  
2. Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **modułów**.  
  
3. W **modułów** oknie Znajdź **adres** kolumny. Może być konieczne sprawdzenie za pomocą paska przewijania.  
  
4. Kliknij przycisk **adres** przycisku w górnej części kolumny, aby sortować biblioteki DLL przy użyciu adresu.  
  
5. Skanowanie posortowaną listę można znaleźć biblioteki DLL, którego zakres adresów zawiera lokalizację awarii.  
  
6. Przyjrzyj się **nazwa** i **ścieżki** kolumny, aby wyświetlić nazwę biblioteki DLL i ścieżkę.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Debugowanie natywnych bibliotek DLL](../debugger/how-to-debug-native-dlls.md)   
 [Instrukcje: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)
