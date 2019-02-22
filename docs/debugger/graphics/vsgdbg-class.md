---
title: VsgDbg Class | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4051a02de6a046621e62c21b4d2399b5a2703cb8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714806"
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
Reprezentuje interfejs dla programistyczną kontrolę składnika w aplikacji, diagnostyki grafiki.

## <a name="syntax"></a>Składnia

```C++
class VsgDbg;
```

## <a name="members"></a>Elementy członkowskie
 `VsgDbg` Klasa obsługuje następujące elementy członkowskie.

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Tworzy wystąpienie klasy `VsgDbg` klasy i opcjonalnie przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|
|[VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienie `VsgDbg` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AddMessage](addmessage.md)|Dodaje niestandardowy komunikat do diagnostyki grafiki HUD (wyświetlanie Head-Up).|
|[BeginCapture](begincapture.md)|Rozpoczyna się interwał przechwytywania, które będą kończyć się znakiem `EndCapture`.|
|[CaptureCurrentFrame](capturecurrentframe.md)|Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.|
|[Kopiowanie (przechwycenie programowe)](copy-programmatic-capture.md)|Kopiuje zawartość active grafiki (.vsglog) pliku do nowego pliku.|
|[EndCapture](endcapture.md)|Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.|
|[Init](init.md)|Przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych.|
|[ToggleHUD](togglehud.md)|Włącza/wyłącza nakładki HUD diagnostyki grafiki, lub wyłączyć.|
|[UnInit](uninit.md)|Kończenie znajdujących się w pliku dziennika grafiki, a następnie zamyka i zwalnia zasoby, które były używane podczas, gdy aplikacja została aktywnie rejestrowanie informacji graficznych.|

## <a name="remarks"></a>Uwagi
 `VsgDbg` Klasa reprezentuje interfejs, który służy do kontrolowania funkcji diagnostyki grafiki programowo. Można użyć niektórych funkcji, nawet wtedy, gdy jesteś nie są aktywnie przechwytywanie i rejestrowanie informacji graficznych; obejmuje to `AddMessage` funkcja elementu członkowskiego i `ToggleHUD` funkcja elementu członkowskiego. Funkcje elementów członkowskich przygotowanie składnika w aplikacji, diagnostyki grafiki, aby rozpocząć lub zatrzymać active przechwytywanie informacji graficznych lub musi zostać wywołana, gdy aplikacja jest aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki.