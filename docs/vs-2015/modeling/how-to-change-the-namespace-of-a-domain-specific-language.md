---
title: 'Instrukcje: zmienianie przestrzeni nazw języka specyficznego dla domeny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671720"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Porady: zmienianie przestrzeni nazw języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić przestrzeń nazw języka specyficznego dla domeny. Należy wprowadzić zmianę w **Eksploratorze DSL**, we właściwościach projektu pakietu DSL i w informacjach o zestawie.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeń nazw języka specyficznego dla domeny

1. W **Eksploratorze DSL**kliknij węzeł **DSL** .

2. W oknie **Właściwości** Zmień właściwość **przestrzeń nazw** .

3. Zapisz rozwiązanie i Przekształć szablony.

4. W menu **projekt** kliknij polecenie **Właściwości DSL**.

     Pojawią się właściwości projektu.

5. Kliknij kartę **aplikacja** .

6. Zmień **domyślną właściwość Namespace** na nową nazwę przestrzeni nazw.

7. Jeśli chcesz również zmienić nazwę zestawu, Zmień **Właściwość Nazwa zestawu.**

8. Jeśli zmieniono nazwę zestawu, Otwórz DslPackage\Package.tt i zaktualizuj ten wiersz:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Jeśli Zapisano kod niestandardowy, pamiętaj o zmianie przestrzeni nazw i odwołań do klas w plikach kodu.

10. Zresetuj wystąpienie eksperymentalne programu Visual Studio.

    1. Usuń **\Users \\ **_{Twoja nazwa}_**\AppData\Local\Microsoft\VisualStudio \\ \* **

    2. W menu **Start** systemu Windows wybierz kolejno pozycje **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**i **Zresetuj wystąpienie eksperymentalne**.

11. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**.

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
