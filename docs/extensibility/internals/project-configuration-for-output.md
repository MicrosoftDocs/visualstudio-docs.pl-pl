---
title: Konfiguracja projektu dla danych wyjściowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706668"
---
# <a name="project-configuration-for-output"></a>Konfigurowanie projektu dla danych wyjściowych
Każda konfiguracja może obsługiwać zestaw procesów kompilacji, które generują elementy wyjściowe, takie jak pliki wykonywalne lub pliki zasobów. Te elementy wyjściowe są prywatne dla użytkownika i mogą być umieszczane w grupach, które łączą powiązane typy danych wyjściowych, takie jak pliki wykonywalne (.exe, .dll, .lib) i pliki źródłowe (.idl, pliki .h).

 Elementy wyjściowe mogą być <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> udostępniane za pomocą metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> i wyliczone z metodami. Jeśli chcesz grupować elementy wyjściowe, projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> należy również zaimplementować interfejs.

 Konstrukcja opracowana przez `IVsOutputGroup` implementowanie umożliwia projektom grupowanie wyników według użycia. Na przykład biblioteka DLL może być zgrupowana z bazą danych programu (PDB).

> [!NOTE]
> Plik PDB zawiera informacje debugowania i jest tworzony, gdy opcja "Generowanie informacji debugowania" jest określona podczas tworzenia .dll lub .exe. Plik pdb jest zwykle generowany tylko dla konfiguracji projektu debugowania.

 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji, która obsługuje, nawet jeśli liczba wyjść zawartych w grupie może się różnić w zależności od konfiguracji. Na przykład biblioteka DLL matt projektu może zawierać mattd.dll i mattd.pdb w konfiguracji debugowania, ale tylko matt.dll w konfiguracji sieci sprzedaży.

 Grupy mają również te same informacje o identyfikatorze, takie jak nazwa kanoniczna, nazwa wyświetlana i informacje o grupach, od konfiguracji do konfiguracji w projekcie. Ta spójność umożliwia wdrażanie i pakowanie, aby kontynuować działanie, nawet jeśli konfiguracje się zmieniają.

 Grupy mogą mieć również kluczowe dane wyjściowe, które umożliwia skróty do pakowania, aby wskazać coś znaczącego. Każda grupa może być pusta w danej konfiguracji, więc nie należy zakładać rozmiaru grupy. Rozmiar (liczba wyjść) każdej grupy w dowolnej konfiguracji może się różnić od rozmiaru innej grupy w tej samej konfiguracji. Może również różnić się od rozmiaru tej samej grupy w innej konfiguracji.

 ![Grafika przedstawiająca grupy wyjściowe](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupy wyjściowe

 Podstawowym zastosowaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfejsu jest zapewnienie dostępu do tworzenia, wdrażania i debugowania obiektów zarządzania i umożliwić projektom swobodę grupowania wyjść. Aby uzyskać więcej informacji na temat korzystania z tego interfejsu, zobacz [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md).

 Na poprzednim diagramie Group Built ma kluczowe dane wyjściowe w konfiguracjach (bD.exe lub b.exe), dzięki czemu użytkownik może utworzyć skrót do built i wiedzieć, że skrót będzie działać niezależnie od wdrożonej konfiguracji. Źródło grupy nie ma danych wyjściowych klucza, więc użytkownik nie może utworzyć do niego skrótu. Jeśli grupa debugów zbudowany ma dane wyjściowe klucza, ale grupa sieci sprzedaży zbudowany nie, to będzie niepoprawna implementacja. Wynika z tego, że jeśli dowolna konfiguracja ma grupę, która nie zawiera żadnych wyjść, a w rezultacie nie ma pliku klucza, to inne konfiguracje z tą grupą, które zawierają dane wyjściowe, nie mogą mieć plików kluczy. Edytory instalatora zakładają, że nazwy kanoniczne i nazwy wyświetlane grup, a także istnienie pliku klucza, nie zmieniają się w zależności od konfiguracji.

 Należy zauważyć, że `IVsOutputGroup` jeśli projekt ma, że nie chce spakować lub wdrożyć, wystarczy nie umieścić tego danych wyjściowych w grupie. Dane wyjściowe nadal można wyliczyć normalnie, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodę, która zwraca wszystkie dane wyjściowe konfiguracji, niezależnie od grupowania.

 Aby uzyskać więcej informacji, `IVsOutputGroup` zobacz implementację w przykładzie projektu niestandardowego w [MPF dla projektów](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
