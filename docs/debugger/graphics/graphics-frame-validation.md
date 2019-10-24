---
title: Sprawdzanie poprawności ramki graficznej | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735495"
---
# <a name="graphics-frame-validation"></a>Sprawdzanie poprawności ramki graficznej
<!-- VERSIONLESS -->
Program Visual Studio 2017 lub nowszy obsługuje narzędzie **walidacji ramek** .  W oknie walidacji ramki są wyświetlane błędy i ostrzeżenia skojarzone z listą zdarzeń.  Aby wyświetlić to okno, zaznacz menu **> widoku walidacji ramki** .

![Weryfikacja ramki](media/gfx_diag_frame_validation.png)

Kliknij przycisk **Uruchom weryfikację** w lewym górnym rogu, aby zainicjować analizę.  Ukończenie tej operacji może potrwać kilka minut, w zależności od złożoności ramki.  Dane, które pojawiają się w tym miejscu, są kombinacją z dwóch źródeł: komunikaty, które są emitowane przez program D3D po włączeniu [warstw zestawu SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) , oraz dane zbierane z wewnętrznego śledzenia stanu narzędzia. Po zakończeniu zobaczysz kilka kolumn danych:

| **Kolumna** | **Opis** |
|------------| - |
| Identyfikator zdarzenia | Identyfikator, który jest mapowany na wpis w oknie [Lista zdarzeń](graphics-event-list.md) . |
| Ważność | Uszkodzenie, błąd, ostrzeżenie, informacje lub komunikat. |
| Kategoria | Zdefiniowane przez aplikację, różne, inicjalizacje, czyszczenie, kompilacja, tworzenie stanu, ustawienie stanu, pobieranie stanu, wykonywanie, manipulowanie zasobami, cieniowanie, nadmiarowe i nieużywane. |
| Komunikat | Wiadomość skojarzona ze zdarzeniem. |
| Zdarzenie | Zdarzenie skojarzone z błędem lub ostrzeżeniem. |

## <a name="see-also"></a>Zobacz także
[Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->