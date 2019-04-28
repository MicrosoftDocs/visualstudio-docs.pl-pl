---
title: Sprawdzanie poprawności klatek grafiki | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ce283e5cbab30b612a02ec447113ad11e206a7f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895873"
---
# <a name="graphics-frame-validation"></a>Weryfikacja ramki grafiki
<!-- VERSIONLESS -->
Visual Studio 2017 i lepsze wsparcie **Weryfikacja ramki** narzędzia.  Weryfikacja ramki okna wyświetla błędy i ostrzeżenia skojarzony z listy zdarzeń.  Aby wyświetlić to okno, wybierz **Widok > Weryfikacja ramki** menu.

![Weryfikacja ramki](media/gfx_diag_frame_validation.png)

Kliknij przycisk **Uruchom weryfikację** przycisk w lewym górnym rogu, aby zainicjować analizy.  Może upłynąć kilka minut w zależności od złożoności ramki.  Danych, który pojawia się w tym miejscu składa się z dwóch źródeł: komunikaty D3D tego samego emituje podczas [warstw zestawu SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) jest włączona i dane, które są zbierane z tego narzędzia stanu wewnętrznego śledzenia. Po wykonaniu tych czynności, zostanie wyświetlony kilku kolumn danych:

| **Kolumny** | **Opis** |
|------------| - |
| Identyfikator zdarzenia | Identyfikator, który mapuje do zapisu w [listy zdarzeń](graphics-event-list.md) okna. |
| Ważność | Uszkodzenie, błąd, ostrzeżenie, informacje lub komunikatu. |
| Kategoria | Aplikacji określone, dodatkowe, inicjowanie, oczyszczania, kompilacji, utworzenia stanu, ustawienie stanu, pobieranie stanu, wykonywania, zasobów manipulacji, programu do cieniowania, nadmiarowe i nieużywane. |
| Komunikat | Komunikat skojarzony ze zdarzeniem. |
| Zdarzenie | Zdarzenie skojarzone z błąd lub ostrzeżenie. |

## <a name="see-also"></a>Zobacz też
[Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->