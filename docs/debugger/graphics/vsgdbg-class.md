---
title: Klasa VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4051a02de6a046621e62c21b4d2399b5a2703cb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895195"
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