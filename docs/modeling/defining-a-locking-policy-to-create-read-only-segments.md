---
title: Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
description: Dowiedz się, jak można zdefiniować zasady dla programu w celu zablokowania części lub całego modelu języka specyficznego dla domeny (DSL), aby można go było odczytać, ale nie zmienić.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385789"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
Interfejs API niezmienności zestawu SDK wizualizacji i modelowania usługi Visual Studio umożliwia programowi zablokowanie części lub całego modelu języka specyficznego dla domeny (DSL), aby można go było odczytać, ale nie zmienić. Tej opcji tylko do odczytu można użyć na przykład, aby użytkownik mógł poprosić współpracowników o adnotację i przejrzenie modelu DSL, ale może nie zezwalać im na zmianę oryginalnego.

 Ponadto, jako autor DSL, można zdefiniować zasady *blokowania.* Zasady blokowania określają, które blokady są dozwolone, niedozwolone lub obowiązkowe. Na przykład podczas publikowania DSL można zachęcić deweloperów innych firm do rozszerzenia go o nowe polecenia. Można jednak również użyć zasad blokowania, aby uniemożliwić im zmianę stanu tylko do odczytu określonych części modelu.

> [!NOTE]
> Zasady blokowania można obejść przy użyciu odbicia. Zapewnia ona wyraźne granice dla deweloperów innych firm, ale nie zapewnia silnego bezpieczeństwa.

 Więcej informacji i przykładów można znaleźć w witrynie Visual Studio [zestawu SDK wizualizacji i modelowania.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Ustawianie i pobieranie blokad
 Blokady można ustawić w magazynie, na partycji lub w jednym elemencie. Na przykład ta instrukcja uniemożliwi usunięcie elementu modelu, a także zapobiegnie zmianie jego właściwości:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Inne wartości blokady mogą służyć do zapobiegania zmianom w relacjach, tworzeniu elementów, poruszaniu się między partycjami i zmienianiu kolejności linków w roli.

 Blokady dotyczą zarówno akcji użytkownika, jak i kodu programu. Jeśli kod programu spróbuje wprowadzić zmianę, `InvalidOperationException` zostanie zgłoszony element . Blokady są ignorowane w operacji Cofnij lub Ponownie.

 Możesz sprawdzić, czy element ma blokadę w danym zestawie, używając elementu , i uzyskać bieżący zestaw blokad elementu `IsLocked(Locks)` za pomocą . `GetLocks()`

 Blokadę można ustawić bez użycia transakcji. Baza danych blokady nie jest częścią magazynu. Jeśli ustawiono blokadę w odpowiedzi na zmianę wartości w magazynie, na przykład w funkcji OnValueChanged, należy zezwolić na zmiany, które są częścią operacji Cofnij.

 Te metody są metodami rozszerzeń zdefiniowanymi w przestrzeni <xref:Microsoft.VisualStudio.Modeling.Immutability> nazw .

### <a name="locks-on-partitions-and-stores"></a>Blokady na partycjach i magazynach
 Blokady można również stosować do partycji i magazynu. Blokada ustawiona na partycji ma zastosowanie do wszystkich elementów w partycji. Dlatego na przykład następująca instrukcja uniemożliwi usunięcie wszystkich elementów w partycji, niezależnie od stanów ich własnych blokad. Niemniej jednak inne blokady, takie `Locks.Property` jak, nadal można ustawić dla poszczególnych elementów:

```csharp
partition.SetLocks(Locks.Delete);
```

 Blokada ustawiona w magazynie ma zastosowanie do wszystkich jej elementów, niezależnie od ustawień tej blokady w partycjach i elementach.

### <a name="using-locks"></a>Używanie blokad
 Blokad można używać do implementowania schematów, takich jak następujące przykłady:

- Nie zezwalaj na zmiany we wszystkich elementach i relacjach z wyjątkiem tych, które reprezentują komentarze. Dzięki temu użytkownicy mogą adnotacji modelu bez jego zmiany.

- Nie zezwalaj na zmiany w partycji domyślnej, ale zezwalaj na zmiany w partycji diagramu. Użytkownik może zmienić rozmieszczenie diagramu, ale nie może zmienić bazowego modelu.

- Nie zezwalaj na zmiany w sklepie z wyjątkiem grupy użytkowników zarejestrowanych w oddzielnej bazie danych. W przypadku innych użytkowników diagram i model są tylko do odczytu.

- Nie zezwalaj na zmiany w modelu, jeśli właściwość logiczna diagramu jest ustawiona na wartość true. Podaj polecenie menu, aby zmienić właściwość. Dzięki temu użytkownicy nie będą przypadkowo wprowadzać zmian.

- Nie zezwalaj na dodawanie i usuwanie elementów i relacji określonych klas, ale zezwalaj na zmiany właściwości. Dzięki temu użytkownicy mają stały formularz, w którym mogą wypełniać właściwości.

## <a name="lock-values"></a>Zablokuj wartości
 Blokady można ustawiać w magazynie, partycji lub poszczególnych elementach Modelu. Blokady to `Flags` wyliczenie: można połączyć jego wartości przy użyciu "&#124;".

- Blokady elementu ModelElement zawsze zawierają blokady jego partycji.

- Blokady partycji zawsze zawierają blokady magazynu.

  Nie można ustawić blokady na partycji lub magazynie i jednocześnie wyłączyć blokadę pojedynczego elementu.

|Wartość|Oznacza to, że `IsLocked(Value)` jeśli wartość jest prawdziwa|
|-|-|
|Brak|Brak ograniczeń.|
|Właściwość|Nie można zmienić właściwości domeny elementów. Nie dotyczy to właściwości generowanych przez rolę klasy domeny w relacji.|
|Dodaj|Nie można tworzyć nowych elementów i linków w partycji ani magazynie.<br /><br /> Nie dotyczy `ModelElement` .|
|Move|Elementu nie można przenosić między partycjami, `element.IsLocked(Move)` jeśli ma wartość true lub jeśli wartość jest `targetPartition.IsLocked(Move)` prawdziwa.|
|Usuń|Nie można usunąć elementu, jeśli ta blokada jest ustawiona na samym elemencie lub na dowolnym elemencie, do którego zostanie rozpropagowane usunięcie, takim jak osadzone elementy i kształty.<br /><br /> Umożliwia `element.CanDelete()` odnajdywanie, czy można usunąć element.|
|Zmienić kolejność|Nie można zmienić kolejności linków w roleplayer.|
|RolePlayer|Nie można zmienić zestawu linków, które pochodzą z tego elementu. Na przykład w tym elemencie nie można osadzić nowych elementów. Nie ma to wpływu na linki, dla których ten element jest obiektem docelowym.<br /><br /> Jeśli ten element jest łączem, nie ma to wpływu na jego źródło i element docelowy.|
|Wszystko|Bitowe OR innych wartości.|

## <a name="locking-policies"></a>Blokowanie zasad
 Jako autor DSL możesz zdefiniować zasady *blokowania*. Zasady blokowania moderują działanie mechanizmu SetLocks(), dzięki czemu można zapobiec ustawianiu określonych blokad lub nakłonić do ustawienia określonych blokad. Zazwyczaj należy użyć zasad blokowania, aby zniechęcić użytkowników lub deweloperów przed przypadkowym naruszeniem zamierzonego użycia DSL w taki sam sposób, jak można zadeklarować zmienną `private` .

 Można również użyć zasad blokowania, aby ustawić blokady dla wszystkich elementów zależnych od typu elementu. Dzieje się tak, ponieważ element jest zawsze wywoływany, gdy element jest tworzony po raz `SetLocks(Locks.None)` pierwszy lub deserializowany z pliku.

 Nie można jednak używać zasad do zmieniania blokad elementu w trakcie jego życia. Aby osiągnąć ten efekt, należy użyć wywołań do `SetLocks()` .

 Aby zdefiniować zasady blokowania, należy:

- Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> klasę .

- Dodaj tę klasę do usług, które są dostępne za pośrednictwem docData dsl.

### <a name="to-define-a-locking-policy"></a>Aby zdefiniować zasady blokowania
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> ma następującą definicję:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Te metody są wywoływane, gdy wywoływane jest wywołanie metody `SetLocks()` w store, partition lub modelElement. W każdej metodzie jest dostarczany proponowany zestaw blokad. Możesz zwrócić proponowany zestaw lub dodać i odjąć blokady.

 Na przykład:

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

 Aby upewnić się, że użytkownicy mogą zawsze usuwać elementy, nawet jeśli inne wywołania kodu `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Aby nie zezwalać na zmianę wszystkich właściwości każdego elementu Klasy MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Aby udostępnić zasady jako usługę
 W `DslPackage` projekcie dodaj nowy plik zawierający kod podobny do następującego przykładu:

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
