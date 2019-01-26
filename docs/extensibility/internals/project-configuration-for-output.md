---
title: Konfiguracja danych wyjściowych projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72660ab5a3c3aedd888f22bdf7db1ef635d5bc34
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069554"
---
# <a name="project-configuration-for-output"></a>Konfigurowanie projektu dla danych wyjściowych
Każdej konfiguracji może obsługiwać zestaw procesów kompilacji, które generują dane wyjściowe elementów, takich jak pliki wykonywalne lub zasobu. Te elementy danych wyjściowych są prywatne dla użytkownika i można umieścić w grupach, które łączą powiązanych typów danych wyjściowych, takich jak pliki wykonywalne (.exe, .dll, .lib) i pliki źródłowe (.idl, pliki .h).  
  
 Dane wyjściowe elementy mogą być udostępniane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod i wyliczenia z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metody. Jeśli chcesz grupować elementy danych wyjściowych projektu powinny również implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfejsu.  
  
 Konstrukcja opracowane przez zaimplementowanie `IVsOutputGroup` umożliwia projekty do grupy danych wyjściowych, zgodnie z użycia. Na przykład biblioteki DLL mogą być pogrupowane ze swojej bazy danych programu (PDB).  
  
> [!NOTE]
>  Plik PDB zawiera informacje o debugowaniu i jest tworzona, gdy określono opcję "Generuj informacje debugowania", podczas kompilowania .dll lub .exe. Plik .pdb zazwyczaj zostanie wygenerowany tylko Konfiguracja projektu debugowania.  
  
 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji, który ją obsługuje, nawet jeśli liczba wyjść zawarty w grupie będzie zależeć od konfiguracja. Na przykład projektu Matt biblioteki DLL mogą dotyczyć mattd.dll i mattd.pdb w konfiguracji debugowania, ale tylko matt.dll w konfiguracji sieci sprzedaży.  
  
 Grupy również mają te same informacje identyfikator, takie jak nazwa kanoniczna, nazwę wyświetlaną i informacje o grupie, konfiguracja konfiguracji w ramach projektu. Ta spójność umożliwia wdrażanie i pakowanie nadal działać, nawet jeśli zmiany konfiguracji.  
  
 Grupy mogą mieć również kluczowe dane wyjściowe, umożliwiająca pakowanie skróty wskazywała na bardziej opisową nazwę. Wszystkie grupy może być pusta w danej konfiguracji, więc należy wprowadzać żadnych założeń o rozmiarze grupy. Rozmiar każdej grupy w żadnej konfiguracji (liczba wyjść) może być różny od rozmiaru innej grupy w tej samej konfiguracji. Również może być różny od rozmiaru tej samej grupy w innej konfiguracji.  
  
 ![Grafika przedstawiająca grupy danych wyjściowych](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupy danych wyjściowych  
  
 Podstawowym zastosowaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfejs jest zapewnienie dostępu do tworzenie, wdrażanie i debugowanie obiektów zarządzania i Zezwalaj projektów swobody grupy danych wyjściowych. Aby uzyskać więcej informacji dotyczących używania tego interfejsu, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md).  
  
 Na poprzednim rysunku wbudowana grupa ma klucz dane wyjściowe konfiguracjach (bD.exe lub b.exe), więc użytkownik może utworzyć skrót do wbudowana i dowiedzieć się, że skrót będzie działać niezależnie od konfiguracji wdrożone. Źródło grupy nie ma klucza z danych wyjściowych, dzięki czemu użytkownik nie może utworzyć skrót do niego. Debugowanie grupy wbudowane ma kluczowe dane wyjściowe, ale wbudowane grupy sprzedaży detalicznej nie, który będzie mieć niepoprawne implementację. Następuje, następnie, jeśli dowolna konfiguracja zawiera grupę zawierającą Brak danych wyjściowych, a co w efekcie nie plik klucza, a następnie inne konfiguracje z tej grupy, które zawierają dane wyjściowe nie mogą mieć pliki klucza. Edytory Instalatora przyjęto założenie, że nazwy kanonicznej i nazw wyświetlanych grup oraz istnienie plik klucza nie zmieniaj zależności w konfiguracji.  
  
 Należy pamiętać, że jeśli projekt ma `IVsOutputGroup` Aby zrezygnować z pakietu lub wdrożenia, jest wystarczające, aby nie można umieścić te dane wyjściowe w grupie. Dane wyjściowe mogą być wyliczane nadal normalnie przez zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodę, która zwraca wszystkie dane wyjściowe konfiguracji, niezależnie od tego, grupowanie.  
  
 Aby uzyskać więcej informacji, zobacz wykonania `IVsOutputGroup` w przykładowym projekcie niestandardowe na [MPF projektów](https://github.com/tunnelvisionlabs/MPFProj10).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)