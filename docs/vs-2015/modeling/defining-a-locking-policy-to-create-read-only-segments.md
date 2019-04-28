---
title: Definiowanie zasad blokowania się tworzenia segmentów tylko do odczytu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6044e9c47a0dcbc95fd1503906cbd81ac8e44526
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422654"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interfejs API niezmienności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wizualizacji i modelowania SDK umożliwia programowi blokady część lub całość model języka specyficznego dla domeny (DSL), aby można go odczytać ale niezmienione. Tej opcji tylko do odczytu może służyć, na przykład, aby poprosić współpracowników, aby dodać adnotacje i przejrzeć modelu DSL użytkownika, ale może zabronić im zmianę oryginału.  
  
 Ponadto, ponieważ autor DSL, można zdefiniować *zasad blokowania.* Zasad blokowania definiuje, które blokady są dozwolone, niedozwolone lub obowiązkowe. Na przykład podczas publikowania DSL może zachęcać deweloperom firm rozbudowuj je przy użyciu nowych poleceń. Ale zasad blokowania można również użyć, aby uniemożliwić zmianę stanu tylko do odczytu określonego części modelu.  
  
> [!NOTE]
> Może zostać ominięte zasad blokowania przy użyciu odbicia. Udostępnia wyraźne granice dla deweloperów innych firm, ale nie zapewnia silne zabezpieczenia.  
  
 Więcej informacji i przykłady są dostępne pod adresem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkId=186128) witryny sieci Web.  
  
## <a name="setting-and-getting-locks"></a>Ustawienie i pobranie blokady  
 Możesz ustawić blokady w sklepie, partycji lub pojedynczego elementu. Na przykład niniejszych uniemożliwi usuwany element modelu i również uniemożliwi jej właściwości zmianę:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Inne wartości blokady może służyć do uniemożliwić zmiany w relacji, utworzenie elementu, przeniesienie między partycjami i ponownie szeregowania łącza w roli.  
  
 Blokady, stosuje się do akcji użytkownika i kodu programu. Jeśli kod programu próbuje wprowadzić zmianę, `InvalidOperationException` zostanie zgłoszony. Blokady są ignorowane w przypadku operacji cofania i ponawiania.  
  
 Można wykryć, czy element ma żadnej blokady w danym zestawie przy użyciu `IsLocked(Locks)` i bieżący zestaw blokady na element można uzyskać za pomocą `GetLocks()`.  
  
 Możesz ustawić blokadę bez przy użyciu transakcji. Blokady bazy danych nie jest częścią magazynu. Jeśli ustawisz blokady w odpowiedzi na zmianę wartości w magazynie, na przykład w OnValueChanged, Zezwól na zmiany, które są częścią operacji cofania.  
  
 Te metody są metody rozszerzające, które są zdefiniowane w <xref:Microsoft.VisualStudio.Modeling.Immutability> przestrzeni nazw.  
  
### <a name="locks-on-partitions-and-stores"></a>Blokad na partycje i magazynami  
 Blokady może również będą stosowane do partycji i magazyn. Lock, który jest ustawiony na partycji ma zastosowanie do wszystkich elementów w partycji. W związku z tym na przykład następująca instrukcja uniemożliwi wszystkie elementy w partycji usuwane niezależnie od tego, Stany własne blokad. Niemniej jednak inne blokuje takich jak `Locks.Property` nadal można ustawić na poszczególne elementy:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Lock, który jest ustawiony na Store ma zastosowanie do wszystkich jego elementów, niezależnie od ustawienia tego blokady na partycje i elementów.  
  
### <a name="using-locks"></a>Użycie blokad  
 Można użyć blokady wdrożenie systemów, takich jak następujące przykłady:  
  
- Nie zezwalaj na zmiany do wszystkich elementów i relacji z wyjątkiem tych, które reprezentują komentarze. Dzięki temu użytkownicy mogą dodawać adnotacje do modelu, nie zmieniając go.  
  
- Nie zezwalaj na zmiany w domyślnej partycji, ale zezwalaj na zmiany w partycji diagramu. Użytkownik może zmienić układ diagramu, ale nie można zmienić modelu źródłowym.  
  
- Nie zezwalaj na zmienianie Store, z wyjątkiem grupy użytkowników, którzy są rejestrowane w oddzielnej bazy danych. Dla innych użytkowników diagramu i modelu są przeznaczone tylko do odczytu.  
  
- Nie zezwalaj na zmiany w modelu, jeśli ustawiono właściwość typu Boolean diagramu na wartość true. Podaj polecenie menu, aby zmienić tę właściwość. Dzięki temu użytkownicy, którzy nie należy wprowadzać zmian przypadkowo.  
  
- Nie zezwalaj na dodawanie i usuwanie elementów i relacji z określonymi klasami, ale zezwalaj na zmiany właściwości. Zapewnia to użytkownikom stały formularza, w którym można wypełnić właściwości.  
  
## <a name="lock-values"></a>Blokady wartości  
 Można ustawić blokady na Store, partycji lub poszczególnych ModelElement. Blokady jest `Flags` wyliczenia: można połączyć wartości za pomocą "&#124;".  
  
- Blokady ModelElement zawsze zawierać blokady jego partycji.  
  
- Blokady partycji zawsze zawierać blokady Store.  
  
  Nie można ustawić blokadę na partycję lub przechowywać i w tym samym czasie wyłączyć blokadę pojedynczego elementu.  
  
|Wartość|Co oznacza, jeśli `IsLocked(Value)` ma wartość true|  
|-----------|------------------------------------------|  
|Brak|Bez ograniczeń.|  
|Właściwość|Nie można zmienić właściwości domeny elementów. To nie ma zastosowania do właściwości, które są generowane przez rolę klasy domeny w relacji.|  
|Dodaj|Nie można utworzyć nowych elementów i łącza w partycji lub przechowywania.<br /><br /> Nie dotyczy `ModelElement`.|  
|Przenieś|Nie można przenieść elementu między partycjami, jeśli `element.IsLocked(Move)` ma wartość true, lub jeśli `targetPartition.IsLocked(Move)` ma wartość true.|  
|Usuwanie|Nie można usunąć elementu, jeśli ustawiono tę blokadę samego elementu lub na każdym z elementów, do którego usunięcia będzie propagował, takich jak elementy osadzone i kształtów.<br /><br /> Możesz użyć `element.CanDelete()` do wykrywania, czy element może zostać usunięty.|  
|Zmiana kolejności|Nie można zmienić kolejności linków na roleplayer.|  
|RolePlayer|Nie można zmienić zestawu łączy, które biorą się w tym elemencie. Na przykład nowe elementy nie mogą być osadzone w ramach tego elementu. Nie ma to wpływu na łącza, dla którego ten element jest element docelowy.<br /><br /> Jeśli ten element jest łączem, jego źródłowe i docelowe nie są zagrożone.|  
|Wszystkie|Bitowe OR inne wartości.|  
  
## <a name="locking-policies"></a>Zasady blokowania  
 Autor DSL, można zdefiniować *zasad blokowania*. Zasady blokowania łagodzi warunki operacji SetLocks(), dzięki czemu można zapobiec blokad określonego zestawu lub zmusza do określonych blokady musi być ustawiona. Zazwyczaj zasad blokowania umożliwiają zniechęcić użytkowników lub deweloperów od przypadkowo naruszeniem zamierzonym użyciem DSL, w taki sam sposób, że można zadeklarować zmienną `private`.  
  
 Można również użyć zasad blokowania można ustawić blokady na wszystkie elementy zależne od typu elementu. Jest to spowodowane `SetLocks(Locks.None)` zawsze jest wywoływany, gdy element najpierw zostanie utworzony lub zdeserializować z pliku.  
  
 Nie można jednak użyć zasad, będzie się różnić blokady na element podczas okresu istnienia. Aby osiągnąć ten efekt, należy użyć wywołania `SetLocks()`.  
  
 Aby zdefiniować zasad blokowania, należy:  
  
- Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
- Dodaj tę klasę do usług, które są dostępne za pośrednictwem DocData DSL.  
  
### <a name="to-define-a-locking-policy"></a>Do definiowania zasad blokowania  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> ma następującą definicję:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Te metody są wywoływane, gdy połączenie jest nawiązywane w przypadku `SetLocks()` na Store, partycji lub ModelElement. W każdej metody są dostarczane z zestawem proponowane blokad. Może zwrócić zestawu proponowanych lub można dodawania i odejmowania blokad.  
  
 Na przykład:  
  
```  
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
  
 Aby upewnić się, że użytkownicy zawsze możesz usunąć elementy, nawet jeśli inne kod wywołuje metodę `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Aby uniemożliwić zmiany we właściwościach każdego elementu MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Aby udostępnić zasady w trybie usługi  
 W swojej `DslPackage` projektu, Dodaj nowy plik, który zawiera kod, który przypomina poniższy przykład:  
  
```  
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
