---
title: 'Instrukcje: Zmiana maszyny odtwarzania diagnostyki grafiki | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0af2fc0c847c88aa4cc7cb0b15a80e9bdfa4703d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723347"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Instrukcje: Zmiana maszyny odtwarzania diagnostyki grafiki
Można odtwarzać informacji graficznych przy użyciu komputera lokalnego lub za pomocą zdalnym komputerze lub urządzeniu.

## <a name="choosing-a-playback-machine"></a>Wybieranie komputera odtwarzania
 Maszyna odtwarzania jest komputerem lub urządzeniem, który służy do odtwarzania zdarzenia grafiki z dziennika grafiki. Zwykle komputer lokalny to najwygodniejsza opcja, ale problem z renderowaniem może być nie do odtworzenia na komputerze, który ma innej sprzętowej lub wersjach sterowników niż komputer, w której został przechwycony; w takiej sytuacji można wybrać zdalny komputer do odtwarzania konfiguracji problemu i nadal używać komputera deweloperskiego do diagnozowania.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Aby użyć komputera lokalnego do odtwarzania informacji graficznych

1.  W oknie dokumentu dziennika grafiki, wybierz **maszynę odtwarzającą** łącza. **Połączenia zdalnego debugera** pojawi się okno dialogowe.

2.  W obszarze **Konfiguracja ręczna**w **adres** właściwości wprowadź `localhost`.

3.  Ustaw **tryb uwierzytelniania** właściwości **Brak**.

4.  Wybierz **wybierz** przycisku.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Aby użyć komputera zdalnego do odtwarzania informacji graficznych

1.  W oknie dokumentu dziennika grafiki, wybierz **maszynę odtwarzającą** łącza. **Połączenia zdalnego debugera** pojawi się okno dialogowe.

2.  W obszarze **Konfiguracja ręczna**w **adres** właściwość, wprowadź nazwę domeny Windows lub adres IP komputera lub urządzenia, które chcesz użyć do odtwarzania informacji graficznych.

3.  Określ rodzaj autoryzacji, którego chcesz użyć do zabezpieczenia połączenia z komputerem odtwarzania.

    -   W przypadku uwierzytelniania Windows ustaw **tryb uwierzytelniania** właściwości **Windows**.

    -   Aby nie używać uwierzytelniania, należy ustawić **tryb uwierzytelniania** właściwości **Brak**.

4.  Wybierz **wybierz** przycisku.

> [!NOTE]
>  **Połączenia zdalnego debugera** okno dialogowe mogą być również wyświetlane obiekty docelowe debugowania zdalnego, które są podłączone bezpośrednio do komputera deweloperskiego lub znajdują się w tej samej podsieci. Można użyć jednej z tych celów zdalnego debugowania jako maszyny odtwarzania diagnostyki grafiki bez ręcznej konfiguracji. W **połączenia zdalnego debugera** okna dialogowego Wybierz element docelowy ma, a następnie wybierz **wybierz** przycisku.

## <a name="see-also"></a>Zobacz też
- [Dokument dziennika grafiki](graphics-log-document.md)