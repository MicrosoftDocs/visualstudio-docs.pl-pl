---
title: 'Przewodnik: Przechwytywanie informacji graficznych | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab86d42cd158ad64ebb16497b8d2d9f5a7002df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734723"
---
# <a name="walkthrough-capturing-graphics-information"></a>Wskazówki: przechwytywanie informacji graficznych
W tym instruktażu przedstawiono sposób użycia Diagnostyka grafiki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do ręcznego przechwytywania informacji graficznych z aplikacji Direct3D.

 Ten Instruktaż ilustruje następujące zadania:

- Podłączanie Diagnostyka grafiki do aplikacji

- Przechwytywanie informacji graficznych

## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
 Aby skorzystać z narzędzi Diagnostyka grafiki, musisz najpierw przechwycić informacje o grafice, na których bazują. Aby włączyć funkcję przechwytywania, użyj polecenia **Uruchom diagnostykę** , aby podłączyć Diagnostyka grafiki do aplikacji podczas jej uruchamiania.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Aby włączyć Przechwytywanie informacji graficznych po załadowaniu projektu lub rozwiązania

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Załaduj plik projektu lub rozwiązania dla aplikacji, z której chcesz przechwytywać informacje graficzne.

2. Na pasku narzędzi Diagnostyka grafiki wybierz pozycję **Rozpocznij diagnostykę**.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Aby włączyć Przechwytywanie informacji graficznych bez ładowania projektu lub rozwiązania

1. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**. Pojawi się okno dialogowe **Otwórz projekt** .

2. Zamiast pliku projektu lub rozwiązania, określ plik wykonywalny dla aplikacji, z której chcesz przechwytywać informacje graficzne, a następnie wybierz **Otwórz**.

3. Na pasku menu wybierz kolejno opcje **Debuguj**, **grafika**i **Uruchom diagnostykę**.

   Po uruchomieniu aplikacji i wyrenderowaniu ramek można przechwytywać informacje o grafice.

#### <a name="to-capture-graphics-information"></a>Aby przechwycić informacje graficzne

- Na pasku narzędzi Diagnostyka grafiki wybierz przycisk **przechwytywania** . ![Ikona przycisku przechwytywania grafiki](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   —lub—

   Korzystając z aplikacji na ostru, naciśnij przycisk **Print Screen**.

  Za każdym razem, gdy przechwytujesz informacje o ramce, Diagnostyka grafiki rejestruje zdarzenia Direct3D i skojarzonego stanu i dodaje te dane do dziennika grafiki. Nowy dziennik grafiki jest tworzony dla każdej sesji Diagnostyka grafiki. Aby uzyskać informacje na temat dzienników grafiki, zobacz [Omówienie](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono sposób ręcznego przechwytywania informacji graficznych. W następnym kroku należy wziąć pod uwagę tę opcję:

- Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi Diagnostyka grafiki. Zobacz [Omówienie](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Zobacz także
- [Przechwytywanie informacji graficznych](capturing-graphics-information.md)