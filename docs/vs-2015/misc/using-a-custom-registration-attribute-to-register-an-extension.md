---
title: Użycie niestandardowego atrybutu rejestracji do zarejestrowania rozszerzenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935787"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Używanie niestandardowego atrybutu rejestracji do rejestrowania rozszerzenia
W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Możesz użyć atrybutów rejestracji, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi być pochodną <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> i musi zastąpić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody i.  
  
## <a name="creating-a-custom-attribute"></a>Tworzenie atrybutu niestandardowego  
 Poniższy kod przedstawia sposób tworzenia nowego atrybutu rejestracji.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>Jest używany w klasach atrybutów do określenia elementu programu (klasy, metody itp.), do którego odnosi się ten atrybut, czy może być używany więcej niż jeden raz i czy może być dziedziczona.  
  
### <a name="creating-a-registry-key"></a>Tworzenie klucza rejestru  
 W poniższym kodzie atrybut niestandardowy tworzy **niestandardowy** podklucz w kluczu dla pakietu VSPackage, który jest rejestrowany.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości w istniejącym kluczu rejestru  
 Możesz dodać wartości niestandardowe do istniejącego klucza. Poniższy kod pokazuje, jak dodać nową wartość do klucza rejestracji pakietu VSPackage.  
  
```  
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