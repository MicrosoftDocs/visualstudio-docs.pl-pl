---
title: Poprzednie wersje programu .NET Framework dla docelowychF#
description: Dowiedz się więcej o przeznaczone dla starszej wersji programu .NET Framework, korzystając z F# w programie Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1b347a5a2ef2ef9e82b65c768b4f8ec331c912d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942079"
---
# <a name="target-older-versions-of-net-f"></a>Docelowa starszej wersji platformy .NET (F#)

Może się pojawić następujący błąd, jeśli zostanie podjęta próba skierowane do .NET Framework 2.0, 3.0 lub 3.5 w F# projektu programu Visual Studio jest zainstalowany w Windows 8.1:

**Ten projekt wymaga 2.0 F# środowiska uruchomieniowego, ale że środowisko uruchomieniowe nie jest zainstalowany.**

Wiadomo, że ten błąd występuje w ramach następujących kombinacji warunków:

- Na Windows 8.1 jest zainstalowany program Visual Studio.

- .NET Framework 3.5 nie zostały włączone, przed zainstalowaniem programu Visual Studio.

- Projekt jest przeznaczony dla .NET Framework 2.0, 3.0 lub 3.5.

Podczas instalowania programu Visual Studio wykrywa zainstalowane wersje programu .NET Framework. Program Visual Studio instaluje F# 2.0 środowisko uruchomieniowe tylko wtedy, gdy program .NET Framework 3.5 jest zainstalowane i włączone.

## <a name="resolve-the-error"></a>Usuń przyczynę błędu

Aby rozwiązać ten problem, można:

- Obiekt docelowy nowszą wersję programu .NET Framework.

- Włącz dla programu .NET Framework 3.5 on Windows 8.1, a następnie zainstaluj F# 2.0 środowisko uruchomieniowe, naprawiając instalację programu Visual Studio. Postępuj zgodnie z instrukcjami, aby to zrobić.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Aby włączyć program .NET Framework 3.5 na Windows 8.1

1. Na **Start** ekranu, wpisz **Panelu sterowania**.

   Podczas wpisywania **Panelu sterowania** ikona pojawia się w obszarze **aplikacje** nagłówka.

2. Wybierz **Panelu sterowania** ikonę, wybierz **programy** ikonę, a następnie wybierz **Windows Włącz lub wyłącz funkcje** łącza.

3. Upewnij się, że **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** pole wyboru jest zaznaczone, a następnie wybierz **OK** przycisku. Nie ma potrzeby zaznacz pole wyboru dla żadnych węzłów podrzędnych dla składników opcjonalnych programu .NET Framework.

   .NET Framework 3.5 jest włączona, jeśli nie była już.

### <a name="to-install-the-f-20-runtime"></a>Aby zainstalować F# 2.0 runtime

Postępuj zgodnie z [kroki w celu naprawy programu Visual Studio 2017](../install/repair-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [F#Przewodnik (.NET Framework)](/dotnet/fsharp/)
- [F#w programie Visual Studio](fsharp-visual-studio.md)