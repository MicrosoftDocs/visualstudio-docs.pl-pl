---
description: Reprezentuje interfejs do kontroli programistycznej składnika w aplikacji diagnostyki grafiki.
title: Klasa VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a4847e0d6c72d4de611edc47481477d2862a55
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160463"
---
# <a name="vsgdbg-class"></a>VsgDbg — Klasa
Reprezentuje interfejs do kontroli programistycznej składnika w aplikacji diagnostyki grafiki.

## <a name="syntax"></a>Składnia

```C++
class VsgDbg;
```

## <a name="members"></a>Elementy członkowskie
 `VsgDbg`Klasa obsługuje następujących członków.

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Konstruuje wystąpienie `VsgDbg` klasy i opcjonalnie przygotowuje składnik aplikacji diagnostyki grafiki w celu aktywnego przechwytywania i rejestrowania informacji graficznych.|
|[VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Niszczy wystąpienie `VsgDbg` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AddMessage](addmessage.md)|Dodaje niestandardowy komunikat do HUD diagnostyki grafiki (wyświetlacz podręczny).|
|[BeginCapture](begincapture.md)|Rozpoczyna Interwał przechwytywania, który zakończy się od `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Przechwytuje resztę bieżącej ramki do pliku dziennika grafiki.|
|[Kopiowanie (przechwycenie programowe)](copy-programmatic-capture.md)|Kopiuje zawartość aktywnego pliku dziennika grafiki (. vsglog) do nowego pliku.|
|[EndCapture](endcapture.md)|Zakończenie interwału przechwytywania, który został uruchomiony z `BeginCapture` .|
|[Init](init.md)|Przygotowuje składnik aplikacji diagnostyki grafiki w celu aktywnego przechwytywania i rejestrowania informacji graficznych.|
|[ToggleHUD](togglehud.md)|Włącza lub wyłącza nakładkę diagnostyki grafiki w HUD.|
|[UnInit](uninit.md)|Kończy plik dziennika grafiki, zamyka go i zwalnia zasoby, które były używane podczas aktywnie rejestrowania informacji graficznych przez aplikację.|

## <a name="remarks"></a>Uwagi
 `VsgDbg`Klasa reprezentuje interfejs, za pomocą którego można programowo kontrolować funkcje diagnostyki grafiki. Niektóre funkcje mogą być używane nawet wtedy, gdy nie są aktywnie przechwytywane i rejestrowane informacje graficzne; obejmuje to `AddMessage` funkcję członkowską i `ToggleHUD` funkcję członkowską. Inne funkcje Członkowskie umożliwiają przygotowanie składnika w aplikacji diagnostyki grafiki do uruchamiania lub zatrzymywania aktywnego przechwytywania informacji graficznych lub muszą być wywoływane, gdy aplikacja aktywnie przechwytuje i nagrywa informacje graficzne w pliku dziennika grafiki.
