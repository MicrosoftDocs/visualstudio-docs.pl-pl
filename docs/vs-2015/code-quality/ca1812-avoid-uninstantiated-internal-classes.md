---
title: 'CA1812: Unikaj klas wewnętrznych bez wystąpień | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543978"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Unikaj klas wewnętrznych bez wystąpień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.

## <a name="rule-description"></a>Opis reguły
 Ta reguła próbuje zlokalizować wywołanie jednego z konstruktorów typu i zgłasza naruszenie, jeśli nie zostanie znalezione żadne wywołanie.

 Następujące typy nie są badane przez tę regułę:

- Typy wartości

- Typy abstrakcyjne

- Wyliczenia

- Delegaci

- Typy tablic emitowane przez kompilator

- Typy, których nie można utworzyć, i definiują `static` `Shared` wyłącznie metody (w Visual Basic).

  Jeśli zastosujesz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> do zestawu, który jest analizowany, ta reguła nie zostanie zastosowana dla żadnych konstruktorów oznaczonych jako, `internal` ponieważ nie można ustalić, czy pole jest używane przez inny `friend` zestaw.

  Mimo że nie można obejść tego ograniczenia w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] analizie kodu, zewnętrzna autonomiczna FxCop nastąpi w wewnętrznych konstruktorach, jeśli każdy `friend` zestaw jest obecny w analizie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń typ lub Dodaj kod, który go używa. Jeśli typ zawiera tylko metody statyczne, należy dodać jeden z następujących elementów do typu, aby uniemożliwić kompilatorowi emitowanie domyślnego publicznego konstruktora wystąpień:

- Konstruktor prywatny dla typów przeznaczonych dla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji 1,0 i 1,1.

- `static`Modyfikator ( `Shared` w Visual Basic) dla typów, których celem jest [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. Zaleca się, aby pominąć to ostrzeżenie w następujących sytuacjach:

- Klasa jest tworzona za pomocą metod odbicia z późnym wiązaniem, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- Klasa jest tworzona automatycznie przez środowisko uruchomieniowe lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Na przykład klasy implementujące <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> lub <xref:System.Web.IHttpHandler?displayProperty=fullName> .

- Klasa jest przenoszona jako parametr typu ogólnego, który ma nowe ograniczenie. Na przykład poniższy przykład zgłosi tę regułę.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  W tych sytuacjach zalecamy Pominięcie tego ostrzeżenia.

## <a name="related-rules"></a>Powiązane reguły
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)
