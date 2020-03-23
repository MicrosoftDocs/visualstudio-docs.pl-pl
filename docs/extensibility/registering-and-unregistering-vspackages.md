---
title: Rejestracja i wyrejestrowanie pakietów VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303184"
---
# <a name="register-and-unregister-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage
Atrybuty są używane do rejestrowania pakietu VSPackage, ale

## <a name="register-a-vspackage"></a>Zarejestruj pakiet VSPackage
 Za pomocą atrybutów można kontrolować rejestrację zarządzanych pakietów VSPackages. Wszystkie informacje rejestracyjne znajdują się w pliku *pkgdef.* Aby uzyskać więcej informacji na temat rejestracji opartej na plikach, zobacz [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 Poniższy kod pokazuje, jak używać standardowych atrybutów rejestracji do rejestrowania vspackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Wyrejestrowyj rozszerzenie
 Jeśli eksperymentujesz z wieloma różnymi pakietami VSPackage i chcesz usunąć je z eksperymentalnego wystąpienia, możesz po prostu uruchomić polecenie **Reset.** **Poszukaj opcji Resetuj eksperymentalne wystąpienie programu Visual Studio** na stronie początkowej komputera lub uruchom to polecenie z wiersza polecenia:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Jeśli chcesz odinstalować rozszerzenie zainstalowane w wystąpieniu programów Visual Studio, przejdź do**pozycji Rozszerzenia i aktualizacje** **narzędzi** > , znajdź rozszerzenie i kliknij przycisk **Odinstaluj**.

 Jeśli z jakiegoś powodu żadna z tych metod nie powiedzie się w odinstalowaniu rozszerzenia, można wyrejestrować zestaw VSPackage z wiersza polecenia w następujący sposób:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Rejestrowanie rozszerzenia za pomocą atrybutu rejestracji niestandardowej

W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Atrybuty rejestracji można użyć, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi pochodzić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>od , i musi <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> zastąpić i metody.

### <a name="create-a-custom-attribute"></a>Tworzenie atrybutu niestandardowego

Poniższy kod pokazuje, jak utworzyć nowy atrybut rejestracji.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Jest <xref:System.AttributeUsageAttribute> używany na klasy atrybutów, aby określić element programu (klasa, metoda, itp.), do którego odnosi się atrybut, czy może być używany więcej niż jeden raz i czy może być dziedziczona.

### <a name="create-a-registry-key"></a>Tworzenie klucza rejestru

W poniższym kodzie atrybut niestandardowy tworzy **niestandardowy** podklucz pod kluczem dla vspackage, który jest zarejestrowany.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości przy istniejącym kluczu rejestru

Do istniejącego klucza można dodawać wartości niestandardowe. Poniższy kod pokazuje, jak dodać nową wartość do klucza rejestracji VSPackage.

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
