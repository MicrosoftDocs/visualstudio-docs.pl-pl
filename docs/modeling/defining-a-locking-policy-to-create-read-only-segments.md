---
title: Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0778df98ff5f9665da7220fe40972c9a8f8d8e1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536087"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
Interfejs API niezmienności w programie Visual Studio Wizualizacja i Modeling SDK umożliwia programowi zablokowanie części lub całego modelu języka specyficznego dla domeny (DSL), który może być odczytywany, ale nie zmieniany. Tej opcji tylko do odczytu można na przykład użyć, aby użytkownik mógł poproś współpracowników o dodawanie adnotacji i przeglądanie modelu DSL, ale może uniemożliwić im zmianę oryginalnego.

 Ponadto jako autor DSL można zdefiniować *zasady blokowania.* Zasady blokowania określają, które blokady są dozwolone, niedozwolone lub obowiązkowe. Na przykład po opublikowaniu DSL można zachęcić deweloperów innych firm do ich rozbudowania z nowymi poleceniami. Można również użyć zasad blokowania, aby uniemożliwić im zmianę stanu tylko do odczytu określonych części modelu.

> [!NOTE]
> Zasady blokowania można obejść przy użyciu odbicia. Zapewnia jasne ograniczenie dla deweloperów innych firm, ale nie zapewnia silnych zabezpieczeń.

 Więcej informacji i przykładów można znaleźć w witrynie internetowej [wizualizacji i modelowania zestawu SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) programu Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Ustawianie i pobieranie blokad
 Można ustawić blokadę dla magazynu, partycji lub pojedynczego elementu. Na przykład ta instrukcja uniemożliwi usunięcie elementu modelu i uniemożliwi zmianę jego właściwości:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Inne wartości blokowania mogą służyć do zapobiegania zmianom w relacjach, tworzeniu elementów, przesunięciu między partycjami oraz zmiany kolejności linków w roli.

 Blokady stosują się do akcji użytkownika i kodu programu. Jeśli kod programu próbuje wprowadzić zmianę, `InvalidOperationException` zostanie zgłoszony. Blokady są ignorowane w operacji cofania lub ponawiania.

 Można stwierdzić, czy element ma jakąkolwiek blokadę w danym zestawie przy użyciu `IsLocked(Locks)` i można uzyskać bieżący zestaw blokad dla elementu przy użyciu `GetLocks()` .

 Można ustawić blokadę bez użycia transakcji. Zablokuj bazę danych nie należy do magazynu. Jeśli ustawisz blokadę w reakcji na zmianę wartości w magazynie, na przykład w OnValueChanged, należy zezwolić na zmiany, które są częścią operacji cofania.

 Te metody to metody rozszerzające, które są zdefiniowane w <xref:Microsoft.VisualStudio.Modeling.Immutability> przestrzeni nazw.

### <a name="locks-on-partitions-and-stores"></a>Blokady w partycjach i sklepach
 Blokady można także stosować do partycji i magazynu. Blokada ustawiona na partycji dotyczy wszystkich elementów w partycji. W związku z tym, na przykład, Poniższa instrukcja uniemożliwi usunięcie wszystkich elementów w partycji, niezależnie od stanu ich własnych blokad. Niemniej jednak inne blokady, takie jak `Locks.Property` można nadal ustawić dla poszczególnych elementów:

```csharp
partition.SetLocks(Locks.Delete);
```

 Blokada ustawiona w sklepie ma zastosowanie do wszystkich jej elementów, niezależnie od ustawień tej blokady partycji i elementów.

### <a name="using-locks"></a>Korzystanie z blokad
 Możesz użyć blokad do implementowania schematów, takich jak następujące przykłady:

- Nie Zezwalaj na zmiany wszystkich elementów i relacji, z wyjątkiem tych, które reprezentują Komentarze. Pozwala to użytkownikom na dodawanie adnotacji do modelu bez zmieniania go.

- Nie Zezwalaj na zmiany w partycji domyślnej, ale Zezwalaj na zmiany na partycji diagramu. Użytkownik może zmienić układ diagramu, ale nie może zmienić modelu bazowego.

- Nie Zezwalaj na zmiany w sklepie, z wyjątkiem grupy użytkowników, którzy są zarejestrowani w osobnej bazie danych. W przypadku innych użytkowników diagram i model są tylko do odczytu.

- Nie Zezwalaj na zmiany modelu, jeśli właściwość logiczna diagramu ma wartość true. Podaj polecenie menu, aby zmienić tę właściwość. Dzięki temu użytkownicy nie mogą przypadkowo wprowadzać zmian.

- Nie Zezwalaj na dodawanie i usuwanie elementów i relacji określonych klas, ale Zezwalaj na zmiany właściwości. Zapewnia to użytkownikom stałą formę, w której mogą wypełnić właściwości.

## <a name="lock-values"></a>Zablokuj wartości
 Blokady można ustawić dla magazynu, partycji lub pojedynczych ModelElement. Blokady są `Flags` wyliczeniem: można połączyć jego wartości przy użyciu elementu "&#124;".

- Blokady elementu ModelElement zawsze obejmują blokady jego partycji.

- Blokady partycji zawsze obejmują blokady magazynu.

  Nie można ustawić blokady dla partycji lub magazynu i w tym samym czasie wyłączyć blokadę dla pojedynczego elementu.

|Wartość|Znaczenie, jeśli `IsLocked(Value)` ma wartość true|
|-|-|
|Brak|Brak ograniczeń.|
|Właściwość|Nie można zmienić właściwości domeny elementów. Nie dotyczy to właściwości, które są generowane przez rolę klasy domeny w relacji.|
|Dodaj|Nie można utworzyć nowych elementów i linków w partycji lub magazynie.<br /><br /> Nie dotyczy `ModelElement` .|
|Move|Nie można przenieść elementu między partycjami `element.IsLocked(Move)` , jeśli ma wartość true, lub jeśli `targetPartition.IsLocked(Move)` ma wartość true.|
|Usuń|Nie można usunąć elementu, jeśli ta blokada została ustawiona w samym elemencie lub na dowolnym z elementów, do których zostanie ono propagowane, takich jak osadzone elementy i kształty.<br /><br /> Można użyć, `element.CanDelete()` Aby stwierdzić, czy element może być usunięty.|
|Zmienić kolejność|Nie można zmienić kolejności linków w RolePlayer.|
|RolePlayer|Nie można zmienić zestawu linków, które są źródłem w tym elemencie. Na przykład nowe elementy nie mogą być osadzone w tym elemencie. Nie ma to wpływu na linki, dla których ten element jest elementem docelowym.<br /><br /> Jeśli ten element jest łączem, jego źródło i cel nie są modyfikowane.|
|Wszystko|Wartości bitowe lub inne.|

## <a name="locking-policies"></a>Zasady blokowania
 Jako autor DSL można zdefiniować *zasady blokowania*. Zasada blokowania powoduje umiarkowane działanie operacji SetLocks (), dzięki czemu można zapobiec ustawianiu określonych blokad lub określić, że należy ustawić określone blokady. Zazwyczaj należy użyć zasad blokowania, aby zniechęcić użytkowników lub deweloperów przed przypadkowe contravening zamierzonym użyciem DSL, w taki sam sposób, w jaki można zadeklarować zmienną `private` .

 Można również użyć zasad blokowania, aby ustawić blokady dla wszystkich elementów zależnych od typu elementu. Jest to spowodowane tym, że `SetLocks(Locks.None)` jest zawsze wywoływana, gdy element jest najpierw tworzony lub deserializowany z pliku.

 Nie można jednak używać zasad do różnicowania blokad w elemencie w trakcie jego życia. Aby osiągnąć ten efekt, należy użyć wywołań do `SetLocks()` .

 Aby zdefiniować zasady blokowania, należy:

- Utwórz klasę implementującą <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> .

- Dodaj tę klasę do usług, które są dostępne za pomocą DocData DSL.

### <a name="to-define-a-locking-policy"></a>Aby zdefiniować zasady blokowania
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>ma następującą definicję:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Metody te są wywoływane w przypadku wywołania `SetLocks()` w sklepie, partycji lub ModelElement. W każdej metodzie są udostępniane proponowane zestawy blokad. Można zwrócić proponowany zestaw lub można dodać i odjąć blokady.

 Przykład:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Aby upewnić się, że użytkownicy mogą zawsze usuwać elementy, nawet jeśli inne wywołania kodu`SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Aby nie zezwalać na zmianę we wszystkich właściwościach każdego elementu MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Aby udostępnić zasady jako usługę
 W `DslPackage` projekcie Dodaj nowy plik zawierający kod, który jest podobny do następującego:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
