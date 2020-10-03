---
title: Obsługa DirectX 12 w programie Visual Studio | Microsoft Docs
description: Użytkownicy DirectX 12 zalecają korzystanie z programu PIX w systemie Windows w celu uzyskania pełnego środowiska debugowania graficznego
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671398"
---
# <a name="directx-12-support-in-visual-studio"></a>Obsługa DirectX 12 w programie Visual Studio

## <a name="directx-12-support"></a>Obsługa DirectX 12

Program Visual Studio Diagnostyka grafiki nie obsługuje gier DirectX 12. W przypadku debugowania graficznego z pełną obsługą DirectX 12 program Visual Studio zaleca program *PIX w systemie Windows*. 

Program PIX w systemie Windows to narzędzie do dostrajania i debugowania wydajności z możliwościami zdalnymi. PIX w systemie Windows oferuje siedem głównych funkcji, które pasują do Twoich potrzeb związanych z debugowaniem graficznym. Debuguj i analizuj wydajność renderowania grafiki Direct3D 12 z przechwytywaniem GPU. Zapoznaj się z wydajnością i wątkami wszystkich procesorów CPU i procesora GPU wykonywanych przez grę przy użyciu przechwycenia chronometrażu. Określ nieefektywność wzorców we/wy dysku tytułu i układu pakietu z przechwytywaniem we/wy pliku.

Naciśnij kolejno klawisze dotyczące debugowania graficznego z [**PIX w systemie Windows**](https://aka.ms/PIXonWindows).

[**Pobierz system PIX w systemie Windows**](https://aka.ms/downloadPIX) lub [ **zapoznaj**się z dokumentacją.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX w systemie Windows

Funkcja PIX w systemie Windows siedem głównych trybów działania:
1. **Przechwytuje procesor GPU** na potrzeby debugowania i analizowania wydajności renderowania grafiki Direct3D 12.
2. **Przechwycenia chronometrażu** w celu poznania wydajności i wątkowości wszystkich procesorów i pracy procesora GPU wykonywanych przez grę oraz do śledzenia użycia pamięci GPU.
3. W celu **przechwycenia podsumowania funkcji** są gromadzone informacje o tym, jak długo działa każda funkcja i jak często są one wywoływane.
4. **Przechwytywanie wykres wywołań** śledzi wykonywanie pojedynczej funkcji.
5. **Przechwycenia alokacji pamięci** zapewnia wgląd w alokacje pamięci wykonywane przez grę.
6. **Przechwytywanie we/wy plików** ułatwia zidentyfikowanie niewydajności wzorców we/wy dysku tytułu i układu pakietu.
7. **Monitor systemu** wyświetla dane liczników w czasie rzeczywistym, gdy gra jest uruchomiona.

Szczegółowe wprowadzenie do programu PIX w systemie Windows jest dostępne [ **tutaj**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
