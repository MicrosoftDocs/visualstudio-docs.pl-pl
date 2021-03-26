---
title: Konfiguracja projektu dla danych wyjściowych | Microsoft Docs
description: Dowiedz się więcej na temat procesów kompilacji, które mogą być obsługiwane przez każdą konfigurację, oraz interfejsów i metod, za pomocą których można udostępnić elementy wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13e37999ad9f3bada375c1897207e1e4c15546e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082013"
---
# <a name="project-configuration-for-output"></a>Konfigurowanie projektu dla danych wyjściowych
Każda konfiguracja może obsługiwać zestaw procesów kompilacji, które generują elementy wyjściowe, takie jak pliki wykonywalne lub zasoby. Te elementy wyjściowe są prywatne dla użytkownika i mogą być umieszczone w grupach łączących powiązane typy danych wyjściowych, takich jak pliki wykonywalne (exe, DLL, lib) i pliki źródłowe (. idl,. h).

 Elementy wyjściowe można udostępnić za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod i wyliczyć z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodami. Gdy chcesz grupować elementy wyjściowe, projekt powinien również implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfejs.

 Konstrukcja opracowana przez implementację `IVsOutputGroup` umożliwia projektom grupowanie danych wyjściowych zgodnie z użyciem. Na przykład biblioteka DLL może być zgrupowana z jej bazą danych programu (PDB).

> [!NOTE]
> Plik PDB zawiera informacje o debugowaniu i jest tworzony, gdy opcja "Generuj informacje o debugowaniu" została określona podczas kompilowania pliku DLL lub exe. Plik. pdb jest zwykle generowany tylko dla konfiguracji projektu debugowania.

 Projekt musi zwracać tę samą liczbę grup dla każdej konfiguracji, która obsługuje, nawet jeśli liczba danych wyjściowych zawartych w grupie może się różnić od konfiguracji do konfiguracji. Na przykład biblioteka DLL otoczki projektu może zawierać mattd.dll i otoczkę. pdb w konfiguracji debugowania, ale zawiera tylko matt.dll w konfiguracji detalicznej.

 Grupy mają również te same informacje o identyfikatorach, takie jak nazwa kanoniczna, nazwa wyświetlana i informacje o grupach, od konfiguracji do konfiguracji w ramach projektu. Ta spójność umożliwia wdrożenie i pakowanie, aby kontynuować działanie nawet w przypadku zmiany konfiguracji.

 Grupy mogą także mieć kluczowe dane wyjściowe, które umożliwiają skróty do pakowania, aby wskazywały na coś znaczące. Każda grupa może być pusta w danej konfiguracji, dlatego nie należy wprowadzać żadnych założeń dotyczących rozmiaru grupy. Rozmiar (Liczba wyjść) każdej grupy w dowolnej konfiguracji może różnić się od rozmiaru innej grupy w tej samej konfiguracji. Może być również różna od rozmiaru tej samej grupy w innej konfiguracji.

 ![Grafika grup wyjściowych](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupy wyjściowe

 Głównym zastosowaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfejsu jest zapewnienie dostępu do kompilowania, wdrażania i debugowania obiektów zarządzania oraz Zezwalanie na projekty w celu swobodnego grupowania danych wyjściowych. Aby uzyskać więcej informacji na temat korzystania z tego interfejsu, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md).

 Na poprzednim diagramie utworzona grupa zawiera dane wyjściowe klucza w różnych konfiguracjach (bD.exe lub b.exe), dzięki czemu użytkownik może utworzyć skrót do skompilowania i wiedzieć, że skrót będzie działał niezależnie od wdrożonej konfiguracji. Źródło grupy nie ma klucza wyjściowego, przez co użytkownik nie może utworzyć skrótu do niego. Jeśli grupa debugowania została skompilowana z kluczem wyjściowym, ale utworzona grupa detaliczna nie ma takiej prawidłowej implementacji. Po wykonaniu tej czynności, jeśli jakakolwiek konfiguracja ma grupę, która nie zawiera żadnych danych wyjściowych, a w rezultacie nie ma pliku klucza, inne konfiguracje z tą grupą, które zawierają dane wyjściowe, nie mogą mieć plików kluczy. W edytorach Instalatora założono, że nazwy kanoniczne i nazwy wyświetlane grup oraz istnienie pliku klucza nie zmieniają się na podstawie konfiguracji.

 Należy pamiętać, że jeśli projekt ma `IVsOutputGroup` nie do spakowania ani wdrożenia, wystarczy umieścić te dane wyjściowe w grupie. Dane wyjściowe nadal mogą być wyliczane normalnie przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metody, która zwraca wszystkie dane wyjściowe konfiguracji, niezależnie od grupowania.

 Aby uzyskać więcej informacji, zobacz Implementacja programu `IVsOutputGroup` w niestandardowym przykładzie projektu w [MPF for](https://github.com/tunnelvisionlabs/MPFProj10)Projects.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
