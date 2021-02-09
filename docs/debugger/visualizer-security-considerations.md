---
title: Zagadnienia dotyczące zabezpieczeń wizualizatora | Microsoft Docs
description: Wizualizator programu Visual Studio debugger musi działać z pełnym zaufaniem. Należy pamiętać o możliwych zagrożeniach bezpieczeństwa i podjąć odpowiednie środki ostrożności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c735fe4a14a0412fbb41b28b5a40e27083c3bca6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884198"
---
# <a name="visualizer-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych
Pisanie wizualizatora wiąże się z potencjalnymi zagrożeniami bezpieczeństwa. Obecnie nie istnieją żadne znane luki w zabezpieczeniach dla tych potencjalnych zagrożeń, ale deweloperzy muszą znać je i podejmować odpowiednie środki ostrożności, jak opisano w tym miejscu, aby zabezpieczyć się przed przyszłymi programami wykorzystującymi te luki.

 Wizualizatory debugera wymagają większych uprawnień niż jest to dozwolone w przypadku aplikacji częściowo zaufanej. Wizualizatory nie będą ładowane po zatrzymaniu w kodzie z częściowym zaufaniem. Aby debugować przy użyciu wizualizatora, należy uruchomić kod z pełnym zaufaniem.

## <a name="possible-malicious-debuggee-component"></a>Możliwy złośliwy składnik debugowanego obiektu
 Wizualizatory składają się z co najmniej dwóch klas: jeden po stronie debugera i jeden po stronie debugowanego obiektu. Wizualizatory są często wdrażane w oddzielnych zestawach umieszczonych w katalogach specjalnych, ale można je również ładować z debugowanego obiektu. W takim przypadku debuger Pobiera kod z debugowanego obiektu i uruchamia go w debugerze z pełnym zaufaniem.

 Uruchamianie kodu po stronie debugowanego obiektu z pełnym zaufaniem sprawia problemy, gdy debugowanego obiektu nie jest w pełni zaufany. Jeśli wizualizator próbuje załadować zestaw częściowego zaufania z debugowanego obiektu do debugera, program Visual Studio zakończy wizualizator.

 Jednak nadal istnieje drobna Luka w zabezpieczeniach. Po stronie debugowanego obiektu można skojarzyć ze stroną debugera, która została załadowana z innego źródła (a nie debugowanego obiektu). Po stronie debugowanego obiektu może nakazać, że zaufany debuger wykona działania w jego imieniu. Jeśli zaufana Klasa debugera uwidacznia mechanizm "Usuń ten plik", na przykład, debugowanego obiektu częściowej relacji zaufania może wywołać ten mechanizm, gdy użytkownik wywoła wizualizator.

 Aby wyeliminować tę lukę w zabezpieczeniach, należy mieć na uwadze interfejsy uwidocznione przez wizualizator.

## <a name="see-also"></a>Zobacz też
- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [Porady: pisanie wizualizatora](create-custom-visualizers-of-data.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)