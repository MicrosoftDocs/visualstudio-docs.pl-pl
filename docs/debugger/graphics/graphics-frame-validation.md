---
title: Sprawdzanie poprawności ramki graficznej | Microsoft Docs
description: Dowiedz się więcej na temat narzędzia sprawdzania poprawności ramki dla grafiki w programie Visual Studio. To narzędzie wyświetla błędy i ostrzeżenia skojarzone z listą zdarzeń.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d52d04565b03d988d5d01a64e561fc0da8a16e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885251"
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

## <a name="see-also"></a>Zobacz też
[Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->