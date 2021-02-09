---
title: Zmień komputer odtwarzania diagnostyki grafiki
description: Odtwórz informacje graficzne z dziennika grafiki przy użyciu komputera lokalnego lub komputera zdalnego lub urządzenia, które lepiej odtwarzają problem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0689238bf30947fa36ff58b969afa35a55003b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889203"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Instrukcje: zmiana maszyny odtwarzania diagnostyki grafiki
Możesz odtworzyć informacje graficzne przy użyciu komputera lokalnego lub komputera zdalnego lub urządzenia.

## <a name="choosing-a-playback-machine"></a>Wybieranie maszyny odtwarzania
 Maszyna odtwarzania jest maszyną lub urządzeniem służącym do odtwarzania zdarzeń graficznych z dziennika grafiki. Zazwyczaj komputer lokalny jest najwygodniejszą opcją, ale problem z renderowaniem może nie być odtwarzany na komputerze, który ma różne wersje sprzętu lub sterowników niż maszyna, na której został przechwycony. w takim przypadku można wybrać maszynę zdalnego odtwarzania, która jeszcze bardziej odtworzy problem, a następnie użyć maszyny deweloperskiej do jej zdiagnozowania.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Aby użyć komputera lokalnego do odtwarzania informacji graficznych

1. W oknie dokumentu dziennika grafiki wybierz łącze **maszyna odtwarzania** . Zostanie wyświetlone okno dialogowe **połączenia zdalnego debugera** .

2. W obszarze **Konfiguracja ręczna**, we właściwości **adres** wprowadź wartość `localhost` .

3. Ustaw wartość **Brak** dla właściwości **tryb uwierzytelniania** .

4. Wybierz przycisk **Wybierz** .

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Aby użyć komputera zdalnego do odtwarzania informacji graficznych

1. W oknie dokumentu dziennika grafiki wybierz łącze **maszyna odtwarzania** . Zostanie wyświetlone okno dialogowe **połączenia zdalnego debugera** .

2. W obszarze **Konfiguracja ręczna**, we właściwości **adres** wprowadź nazwę domeny systemu Windows lub adres IP komputera lub urządzenia, które mają być używane do odtwarzania informacji graficznych.

3. Określ rodzaj autoryzacji, która ma być używana do zabezpieczenia połączenia z maszyną odtwarzania.

    - Dla opcji uwierzytelnianie systemu Windows Ustaw właściwość **tryb uwierzytelniania** na **Windows**.

    - W przypadku braku uwierzytelniania ustaw właściwość **tryb uwierzytelniania** na **Brak**.

4. Wybierz przycisk **Wybierz** .

> [!NOTE]
> W oknie dialogowym **połączenia debugera zdalnego** mogą być również wyświetlane elementy docelowe zdalnego debugowania, które są bezpośrednio połączone z maszyną deweloperskią lub znajdują się w tej samej podsieci. Można użyć jednego z tych zdalnych elementów docelowych debugowania jako maszyny odtwarzania Diagnostyka grafiki bez ręcznej konfiguracji. W oknie dialogowym **połączenia debugera zdalnego** wybierz żądany obiekt docelowy, a następnie wybierz przycisk **Wybierz** .

## <a name="see-also"></a>Zobacz też
- [Dokument dziennika grafiki](graphics-log-document.md)