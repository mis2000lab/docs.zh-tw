---
title: 如何：從全域組件快取移除組件
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>如何：從全域組件快取移除組件
從全域組件快取 (GAC) 移除組件的方式有兩種：  
  
-   使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。 若要解除安裝開發和測試期間放在 GAC 中的組件，可使用這個選項。  
  
-   使用 [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)。 若要解除安裝測試安裝套件時及針對生產系統所使用的組件，則應該使用這個選項。  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>使用 Gacutil.exe 移除組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     **gacutil –u** \<*組件名稱*>  
  
     在這個命令中，「組件名稱」是要從全域組件快取移除的組件名稱。  
  
    > [!WARNING]
    >  您不應該使用 Gacutil.exe 移除生產系統上的組件，因為某個應用程式可能仍需要這個組件。 您應該改用 Windows Installer，以維護安裝在 GAC 中之每個組件的參考計數。  
  
 下列範例會從全域組件快取移除名為 `hello.dll` 的組件。  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>使用 Windows Installer 移除組件  
  
1.  從 [控制台] 中的 [程式和功能] 應用程式，選取您要解除安裝的應用程式。 如果安裝套件將組件放在 GAC 中，Windows Installer 會在其他應用程式未使用這些組件時，將組件移除。  
  
    > [!NOTE]
    >  Windows Installer 會維護安裝在 GAC 中之組件的參考計數。 只有在組件的參考計數到達零時 (表示 Windows Installer 套件所安裝的任何應用程式都未使用這個組件)，才能從 GAC 中移除組件。  
  
## <a name="see-also"></a>請參閱  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [操作說明：將組件安裝到全域組件快取](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
