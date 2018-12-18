---
title: VsgDbg, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fb4a830c6cc3af49dcb3e26c6711af1a014c9c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724906"
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reprezentuje interfejs dla programistyczną kontrolę składnika w aplikacji, diagnostyki grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `VsgDbg` Klasa obsługuje następujące elementy członkowskie.  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)|Tworzy wystąpienie klasy `VsgDbg` klasy i opcjonalnie przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|  
|[VsgDbg::~VsgDbg (Destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienie `VsgDbg` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Dodaje niestandardowy komunikat do diagnostyki grafiki HUD (wyświetlanie Head-Up).|  
|[BeginCapture](../debugger/begincapture.md)|Rozpoczyna się interwał przechwytywania, które będą kończyć się znakiem `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.|  
|[Kopiowanie (przechwycenie programowe)](../debugger/copy-programmatic-capture.md)|Kopiuje zawartość active grafiki (.vsglog) pliku do nowego pliku.|  
|[EndCapture](../debugger/endcapture.md)|Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.|  
|[Init](../debugger/init.md)|Przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|  
|[ToggleHUD](../debugger/togglehud.md)|Włącza/wyłącza nakładki HUD diagnostyki grafiki, lub wyłączyć.|  
|[UnInit](../debugger/uninit.md)|Kończenie znajdujących się w pliku dziennika grafiki, a następnie zamyka i zwalnia zasoby, które były używane podczas, gdy aplikacja została aktywnie rejestrowanie informacji graficznych.|  
  
## <a name="remarks"></a>Uwagi  
 `VsgDbg` Klasa reprezentuje interfejs, który służy do kontrolowania funkcji diagnostyki grafiki programowo. Można użyć niektórych funkcji, nawet wtedy, gdy jesteś nie są aktywnie przechwytywanie i rejestrowanie informacji graficznych; obejmuje to `AddMessage` funkcja elementu członkowskiego i `ToggleHUD` funkcja elementu członkowskiego. Funkcje elementów członkowskich przygotowanie składnika w aplikacji, diagnostyki grafiki, aby rozpocząć lub zatrzymać active przechwytywanie informacji graficznych lub musi zostać wywołana, gdy aplikacja jest aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki.



