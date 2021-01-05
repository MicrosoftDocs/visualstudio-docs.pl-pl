---
title: Rejestrowanie i Wyrejestrowywanie pakietów VSPackage | Microsoft Docs
description: Dowiedz się więcej o rejestrowaniu i wyrejestrowywaniu pakietów VSPackage, w tym o używanych atrybutach i pliku. pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b60844826387c2807eedcb47fe24c11a58af80f
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862877"
---
# <a name="register-and-unregister-vspackages"></a>Zarejestruj i Wyrejestruj pakietów VSPackage
Używasz atrybutów do zarejestrowania pakietu VSPackage, ale

## <a name="register-a-vspackage"></a>Rejestrowanie pakietu VSPackage
 Za pomocą atrybutów można kontrolować rejestrację zarządzanych pakietów VSPackage. Wszystkie informacje o rejestracji są zawarte w pliku *. pkgdef* . Aby uzyskać więcej informacji na temat rejestracji na podstawie plików, zobacz [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 Poniższy kod pokazuje, jak używać standardowych atrybutów rejestracji do rejestrowania pakietu VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Wyrejestruj rozszerzenie
 Jeśli eksperymentowanie zostało wykonane z dużą ilością pakietów VSPackage i chcesz je usunąć z wystąpienia eksperymentalnego, można po prostu uruchomić polecenie **Reset** . Wyszukaj pozycję **Zresetuj wystąpienie eksperymentalne programu Visual Studio** na stronie startowej komputera lub Uruchom to polecenie w wierszu polecenia:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Jeśli chcesz odinstalować rozszerzenie, które zostało zainstalowane w wystąpieniu deweloperskim programu Visual Studio, przejdź do pozycji **Narzędzia**  >  **rozszerzenia i aktualizacje**, Znajdź rozszerzenie, a następnie kliknij przycisk **Odinstaluj**.

 Jeśli z jakiegoś powodu żadna z tych metod nie powiedzie się po odinstalowaniu rozszerzenia, można wyrejestrować zestaw pakietu VSPackage z wiersza polecenia w następujący sposób:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Użyj niestandardowego atrybutu rejestracji do zarejestrowania rozszerzenia

W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Możesz użyć atrybutów rejestracji, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi być pochodną <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> i musi zastąpić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody i.

### <a name="create-a-custom-attribute"></a>Tworzenie atrybutu niestandardowego

Poniższy kod przedstawia sposób tworzenia nowego atrybutu rejestracji.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>Jest używany w klasach atrybutów do określenia elementu programu (klasy, metody itp.), do którego odnosi się ten atrybut, czy może być używany więcej niż jeden raz i czy może być dziedziczona.

### <a name="create-a-registry-key"></a>Utwórz klucz rejestru

W poniższym kodzie atrybut niestandardowy tworzy **niestandardowy** podklucz w kluczu dla pakietu VSPackage, który jest rejestrowany.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Utwórz nową wartość w istniejącym kluczu rejestru

Możesz dodać wartości niestandardowe do istniejącego klucza. Poniższy kod pokazuje, jak dodać nową wartość do klucza rejestracji pakietu VSPackage.

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
