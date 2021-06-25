---
title: Konfiguracja projektu dla danych wyjściowych | Microsoft Docs
description: Dowiedz się więcej o procesach kompilacji, które może obsługiwać każda konfiguracja, oraz interfejsach i metodach, za pomocą których mogą być udostępniane elementy wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899878"
---
# <a name="project-configuration-for-output"></a>Konfigurowanie projektu dla danych wyjściowych
Każda konfiguracja może obsługiwać zestaw procesów kompilacji, które tworzyć elementy wyjściowe, takie jak pliki wykonywalne lub pliki zasobów. Te elementy wyjściowe są prywatne dla użytkownika i mogą być umieszczane w grupach, które łączy powiązane typy danych wyjściowych, takie jak pliki wykonywalne (.exe, .dll, lib) i pliki źródłowe (pliki idl, h).

 Elementy wyjściowe mogą być udostępniane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod i wyliczane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metod . Gdy chcesz grupować elementy wyjściowe, projekt powinien również implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfejs.

 Konstrukcja opracowana przez implementację `IVsOutputGroup` umożliwia projektom grupowanie danych wyjściowych zgodnie z użyciem. Na przykład biblioteka DLL może być pogrupowana z bazą danych programu (PDB).

> [!NOTE]
> Plik PDB zawiera informacje debugowania i jest tworzony po określonej opcji "Generuj informacje debugowania" podczas budowania .dll lub .exe. Plik .pdb jest zwykle generowany tylko dla konfiguracji projektu debugowania.

 Projekt musi zwrócić taką samą liczbę grup dla każdej konfiguracji, która jest przez niego wspierana, mimo że liczba danych wyjściowych zawartych w grupie może się różnić w zależności od konfiguracji. Na przykład biblioteka DLL Matta projektu może zawierać pliki mattd.dll i mattd.pdb w konfiguracji debugowania, ale matt.dll tylko w konfiguracji handlu detalicznego.

 Grupy mają również te same informacje o identyfikatorze, takie jak nazwa kanonicka, nazwa wyświetlana i informacje o grupie, od konfiguracji do konfiguracji w projekcie. Ta spójność umożliwia kontynuowanie wdrażania i pakowania nawet w przypadku zmiany konfiguracji.

 Grupy mogą również mieć kluczowe dane wyjściowe, które umożliwiają skróty do pakowania, aby wskazać coś znaczącego. Każda grupa może być pusta w danej konfiguracji, więc nie należy zakładać rozmiaru grupy. Rozmiar (liczba danych wyjściowych) każdej grupy w dowolnej konfiguracji może różnić się od rozmiaru innej grupy w tej samej konfiguracji. Może również różnić się od rozmiaru tej samej grupy w innej konfiguracji.

 ![Grafika przedstawiająca grupy danych wyjściowych](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupy wyjściowe

 Podstawowym zastosowaniem interfejsu jest zapewnienie dostępu do kompilowania, wdrażania i debugowania obiektów zarządzania oraz umożliwienie projektom <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> swobodnego grupowania danych wyjściowych. Aby uzyskać więcej informacji na temat korzystania z tego interfejsu, zobacz [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Na poprzednim diagramie grupa zbudowana ma kluczowe dane wyjściowe między konfiguracjami (bD.exe lub b.exe), dzięki czemu użytkownik może utworzyć skrót do wbudowane i wiedzieć, że skrót będzie działać niezależnie od wdrożonej konfiguracji. Źródło grupy nie ma danych wyjściowych klucza, więc użytkownik nie może utworzyć skrótu do niego. Jeśli grupa debugowania sbudowaną ma kluczowe dane wyjściowe, ale grupa handlu detalicznego nie jest sbudowaną, będzie to niepoprawna implementacja. W związku z tym, jeśli dowolna konfiguracja ma grupę, która nie zawiera żadnych danych wyjściowych, a w związku z tym nie ma pliku klucza, inne konfiguracje z tej grupy, które zawierają dane wyjściowe, nie mogą mieć plików kluczy. Edytory instalatorów zakładają, że nazwy kanoniczne i nazwy wyświetlane grup oraz istnienie pliku klucza nie zmieniają się w oparciu o konfiguracje.

 Należy pamiętać, że jeśli projekt ma element , którego nie chce pakować ani wdrażać, wystarczy, aby nie umieścić tych danych wyjściowych `IVsOutputGroup` w grupie. Dane wyjściowe można nadal wyliczać normalnie, implementując metodę , która zwraca wszystkie dane wyjściowe konfiguracji niezależnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> od grupowania.

 Aby uzyskać więcej informacji, zobacz implementację w przykładowym projekcie `IVsOutputGroup` niestandardowym w pliku [MPF for Projects.](https://github.com/tunnelvisionlabs/MPFProj10)

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
