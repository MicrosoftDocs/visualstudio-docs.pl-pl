---
title: Klasa VsgDbg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145695"
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reprezentuje interfejs do kontroli programistycznej składnika w aplikacji diagnostyki grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `VsgDbg`Klasa obsługuje następujących członków.  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)|Konstruuje wystąpienie `VsgDbg` klasy i opcjonalnie przygotowuje składnik aplikacji diagnostyki grafiki w celu aktywnego przechwytywania i rejestrowania informacji graficznych.|  
|[VsgDbg::~VsgDbg (Destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienie `VsgDbg` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Dodaje niestandardowy komunikat do HUD diagnostyki grafiki (wyświetlacz podręczny).|  
|[BeginCapture](../debugger/begincapture.md)|Rozpoczyna Interwał przechwytywania, który zakończy się od `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Przechwytuje resztę bieżącej ramki do pliku dziennika grafiki.|  
|[Kopiowanie (przechwycenie programowe)](../debugger/copy-programmatic-capture.md)|Kopiuje zawartość aktywnego pliku dziennika grafiki (. vsglog) do nowego pliku.|  
|[EndCapture](../debugger/endcapture.md)|Zakończenie interwału przechwytywania, który został uruchomiony z `BeginCapture` .|  
|[Init](../debugger/init.md)|Przygotowuje składnik aplikacji diagnostyki grafiki w celu aktywnego przechwytywania i rejestrowania informacji graficznych.|  
|[ToggleHUD](../debugger/togglehud.md)|Włącza lub wyłącza nakładkę diagnostyki grafiki w HUD.|  
|[UnInit](../debugger/uninit.md)|Kończy plik dziennika grafiki, zamyka go i zwalnia zasoby, które były używane podczas aktywnie rejestrowania informacji graficznych przez aplikację.|  
  
## <a name="remarks"></a>Uwagi  
 `VsgDbg`Klasa reprezentuje interfejs, za pomocą którego można programowo kontrolować funkcje diagnostyki grafiki. Niektóre funkcje mogą być używane nawet wtedy, gdy nie są aktywnie przechwytywane i rejestrowane informacje graficzne; obejmuje to `AddMessage` funkcję członkowską i `ToggleHUD` funkcję członkowską. Inne funkcje Członkowskie umożliwiają przygotowanie składnika w aplikacji diagnostyki grafiki do uruchamiania lub zatrzymywania aktywnego przechwytywania informacji graficznych lub muszą być wywoływane, gdy aplikacja aktywnie przechwytuje i nagrywa informacje graficzne w pliku dziennika grafiki.
