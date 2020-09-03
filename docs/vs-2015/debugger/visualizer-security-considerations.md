---
title: Zagadnienia dotyczące zabezpieczeń wizualizatora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51c79c34520c36e51599d4d6135784f493673b62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146468"
---
# <a name="visualizer-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pisanie wizualizatora wiąże się z potencjalnymi zagrożeniami bezpieczeństwa. Obecnie nie istnieją żadne znane luki w zabezpieczeniach dla tych potencjalnych zagrożeń, ale deweloperzy muszą znać je i podejmować odpowiednie środki ostrożności, jak opisano w tym miejscu, aby zabezpieczyć się przed przyszłymi programami wykorzystującymi te luki.  
  
 Wizualizatory debugera wymagają większych uprawnień niż jest to dozwolone w przypadku aplikacji częściowo zaufanej. Wizualizatory nie będą ładowane po zatrzymaniu w kodzie z częściowym zaufaniem. Aby debugować przy użyciu wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
## <a name="possible-malicious-debuggee-component"></a>Możliwy złośliwy składnik debugowanego obiektu  
 Wizualizatory składają się z co najmniej dwóch klas: jeden po stronie debugera i jeden po stronie debugowanego obiektu. Wizualizatory są często wdrażane w oddzielnych zestawach umieszczonych w katalogach specjalnych, ale można je również ładować z debugowanego obiektu. W takim przypadku debuger Pobiera kod z debugowanego obiektu i uruchamia go w debugerze z pełnym zaufaniem.  
  
 Uruchamianie kodu po stronie debugowanego obiektu z pełnym zaufaniem sprawia problemy, gdy debugowanego obiektu nie jest w pełni zaufany. Jeśli wizualizator próbuje załadować zestaw częściowego zaufania z debugowanego obiektu do debugera, program Visual Studio zakończy wizualizator.  
  
 Jednak nadal istnieje drobna Luka w zabezpieczeniach. Po stronie debugowanego obiektu można skojarzyć ze stroną debugera, która została załadowana z innego źródła (a nie debugowanego obiektu). Po stronie debugowanego obiektu może nakazać, że zaufany debuger wykona działania w jego imieniu. Jeśli zaufana Klasa debugera uwidacznia mechanizm "Usuń ten plik", na przykład, debugowanego obiektu częściowej relacji zaufania może wywołać ten mechanizm, gdy użytkownik wywoła wizualizator.  
  
 Aby wyeliminować tę lukę w zabezpieczeniach, należy mieć na uwadze interfejsy uwidocznione przez wizualizator.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Instrukcje: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
