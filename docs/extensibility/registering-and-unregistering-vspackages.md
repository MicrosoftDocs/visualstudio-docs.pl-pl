---
title: Rejestrowanie i wyrejestrowywanie pakietów VSPackage | Microsoft Docs
description: Dowiedz się więcej na temat rejestrowania i wyrejestrowywania pakietów VSPackage, w tym atrybutów, których używasz, i pliku pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48067ed883a44870b3b753cb5e3d6943eca91ca5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900307"
---
# <a name="register-and-unregister-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage
Atrybuty są rejestrowane za pomocą pakietów VSPackage, ale

## <a name="register-a-vspackage"></a>Rejestrowanie pakietów VSPackage
 Za pomocą atrybutów można kontrolować rejestrację zarządzanych pakietów VSPackage. Wszystkie informacje o rejestracji znajdują się w *pliku pkgdef.* Aby uzyskać więcej informacji na temat rejestracji opartej na plikach, [zobacz Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 Poniższy kod pokazuje, jak za pomocą standardowych atrybutów rejestracji zarejestrować pakiet VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Wyrejestrowywuj rozszerzenie
 Jeśli eksperymentowano z różnymi pakietami VSPackage i chcesz usunąć je z wystąpienia eksperymentalnego, możesz po prostu uruchomić **polecenie Resetuj.** Poszukaj polecenia **Resetuj Visual Studio eksperymentalne** na stronie startowej komputera lub uruchom to polecenie z wiersza polecenia:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Jeśli chcesz odinstalować rozszerzenie zainstalowane w wystąpieniu dewelopera programu Visual Studio, przejdź do menu Rozszerzenia i aktualizacje narzędzi, znajdź rozszerzenie  >  i kliknij przycisk **Odinstaluj.**

 Jeśli z jakiegoś powodu żadna z tych metod nie powiedzie się podczas odinstalowywania rozszerzenia, można wyrejestrować zestaw VSPackage z wiersza polecenia w następujący sposób:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Rejestrowanie rozszerzenia przy użyciu niestandardowego atrybutu rejestracji

W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Atrybutów rejestracji można używać do dodawania nowych kluczy rejestru lub dodawania nowych wartości do istniejących kluczy. Nowy atrybut musi pochodzić od <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , i musi przesłonić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> metody i <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Tworzenie atrybutu niestandardowego

Poniższy kod pokazuje, jak utworzyć nowy atrybut rejestracji.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Klasa jest używana w klasach atrybutów w celu określenia elementu programu (klasy, metody itp.), do którego odnosi się atrybut, czy może być używany więcej niż raz i czy może być <xref:System.AttributeUsageAttribute> dziedziczony.

### <a name="create-a-registry-key"></a>Tworzenie klucza rejestru

W poniższym kodzie atrybut niestandardowy  tworzy niestandardowy podklucz w kluczu dla rejestrowanego pakietów VSPackage.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości w ramach istniejącego klucza rejestru

Wartości niestandardowe można dodać do istniejącego klucza. Poniższy kod pokazuje, jak dodać nową wartość do klucza rejestracji vsPackage.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
