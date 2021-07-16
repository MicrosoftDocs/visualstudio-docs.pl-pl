---
description: Reprezentuje interfejs do programowej kontroli składnika diagnostyki grafiki w aplikacji.
title: VsgDbg, klasa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bb3a9009c38da483b0792b89c115c2e8e9908eb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232456"
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
Reprezentuje interfejs do programowej kontroli składnika diagnostyki grafiki w aplikacji.

## <a name="syntax"></a>Składnia

```C++
class VsgDbg;
```

## <a name="members"></a>Elementy członkowskie
 Klasa `VsgDbg` obsługuje następujące składowe.

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Tworzy wystąpienie klasy i opcjonalnie przygotowuje składnik w aplikacji diagnostyki grafiki do aktywnego przechwytywania `VsgDbg` i nagrywania informacji graficznych.|
|[VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienie `VsgDbg` klasy .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AddMessage](addmessage.md)|Dodaje niestandardowy komunikat do graficznego obrazu HUD (Head-Up Display).|
|[BeginCapture](begincapture.md)|Rozpoczyna interwał przechwytywania, który kończy się na `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Przechwytuje pozostałą część bieżącej ramki do pliku dziennika grafiki.|
|[Kopiowanie (przechwycenie programowe)](copy-programmatic-capture.md)|Kopiuje zawartość aktywnego pliku dziennika grafiki (vsglog) do nowego pliku.|
|[EndCapture](endcapture.md)|Kończy interwał przechwytywania, który został uruchomiony z `BeginCapture` .|
|[Init](init.md)|Przygotowuje składnik diagnostyki grafiki w aplikacji do aktywnego przechwytywania i nagrywania informacji graficznych.|
|[ToggleHUD](togglehud.md)|Włącza lub wyłącza nakładkę HUD diagnostyki grafiki.|
|[UnInit](uninit.md)|Finalizuje plik dziennika grafiki, zamyka go i zamyka zasoby, które były używane podczas aktywnego rejestrowania informacji graficznych przez aplikację.|

## <a name="remarks"></a>Uwagi
 Klasa `VsgDbg` reprezentuje interfejs, który umożliwia programowe sterowanie funkcjami diagnostyki grafiki. Niektórych funkcji można używać nawet wtedy, gdy nie są aktywnie przechwytywane i rejestrowania informacji graficznych; Obejmuje to funkcję `AddMessage` składową i `ToggleHUD` funkcję składową. Inne funkcje członkowskie przygotowują składnik diagnostyki grafiki w aplikacji do uruchomienia lub zatrzymania aktywnego przechwytywania informacji graficznych lub muszą być wywoływane, gdy aplikacja aktywnie przechwytuje i rejestruje informacje graficzne w pliku dziennika grafiki.
