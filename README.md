# Craft-optimization
The ultimate optimizations guide for your favourite block game.


To begin lets start with some things we wont need mods for. 




GENERAL

For the best performance I would hightly suggest using a third party launcher like ATLAUNCHER or PRISM launcher. They allow the ability to have much more customization on a per profile basis. Allowing individual packs to have they're own memory allocation and JVM ARGUMENTS.


ATLAUNCHER: https://atlauncher.com/

PRISM LAUNCHER: https://prismlauncher.org/


MEMORY:

Minecraft is very memory dependent. In a lot of cases memory can make the difference between a playable and not playble experience. 

its highly recommended you add at least 2048mb of memory. When adding more memory use intervals of 1024 so if you are looking to add 8gb it would be 1024 x 8. So your memory amount would be 8192mb. Its suggested that unless absolutely required you use no more than
10gb. More than that can cause issues in java.



JAVA: 
https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA17_22_3_1/graalvm-ee-java17-windows-amd64-22.3.1.zip

Java will need to be on the proper version to use the upcoming JVM Arguments. The Java version id suggest is this version of JDK 17. There are other custom java variants, do your own research and make a decision based upon what you need. 



JVM ARGUMENTS

We are going to be using one of two new Garbage Collectors. If you arent aware, the garbage collector is used for memory management and allocation. A more modern and optimized GC can not only lead to higher FPS but much better frametimes and better performace especially in big modpacks. 


ZGC: This is the GC id suggest. It works the best on modern system but will require a cpu with at least 6 cores and 16gb of ram to work correctly. For anymore information id highly suggest this github for more information on ZGC. https://github.com/1ByteBit/ZGC-For-Minecraft


Shenendoah: This will work for anyone else who has issues with ZGC. It works well with higher memory amounts. id suggest to use this if you are running a pack that facilitates more than 10gb of memory.


ZGC JVM: -XX:+UseZGC -XX:AllocatePrefetchStyle=1 -XX:-ZProactive -XX:ConcGCThreads=4



Shenendoah JVM: -XX:+UseShenandoahGC -XX:ShenandoahGCMode=iu -XX:ShenandoahGuaranteedGCInterval=1000000 -XX:AllocatePrefetchStyle=1



Depending on which GC you plan on using, add those arguments to the JVM arguements below for the full optimization.


JVM ARGUMENTS:
-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1


(Optional)

Large Pages: -XX:+UseLargePages -XX:LargePageSizeInBytes=2m


This is a feature that windows does allow that can allow your page file to dynamically change based on the application running. It can have MASSIVE performance gains but has to be manually enabled in windows and added to the JVM ARGUMENTS. When running minecraft with this, you will need to run it and the launcher as administrator. 

How to enable it: https://www.chaoticafractals.com/manual/getting-started/enabling-large-page-support-windows



DRIVERS:

Update your drivers, gpu and platform drivers are important for overall performance.



Nvidia Control Panel: 

If you have a nvidia gpu and right click on your desktop you should see nvidia control panel. Open it and go to 3D Settings. Once there the settings you are looking to change are:

Power Management: Perfer Max Performance

Threaded Optimization: Enabled

Shader Cache: Unlimited

Low Latency: On (Not ultra unless you are using gsync)



Power Plan:

Search in windows for Power Plan. You should see a battery icon and an optin that says change power plan. Om that screen there should be a little arrow and when clicked you will see another plan called "Max performance plan" Enable that. That will make a big difference on laptops or older ryzen cpus.






MODS

Id like to be able to link a pack and call it a day but so many mods are split between curseforge and modrinth that at this point it would be easier for me to list them off one by one. These mods listed are compatible with Fabric 1.20.1.



LIST:

Sodium/Sodium Extra/Reeses Sodium options

Lithium (Internal server optimizations)

Resolution+ (Lets you control internal resolution) 

Starlight (Redoes the lighting engine)
ImmediatelyFast (Optimizes minecrafts memory stack and immediate mode rendering)

FerriteCore (Memory Optimization)

LazyDFU (Boot optimizations)

C2ME (Chunk Performance, id suggest only using this on servers with support for it as it can cause issues.)

Better Render distance FPS (makes render distance work vertically to cull even more blocks)

More Culling (Self explanitory)

Exordium (lowers fps of UI to give a bit of extra boost)

ksysix (Loads worlds 4 times as fast)

Nvidium (ONLY WORKS ON GTX 16xx AND NEWER)

Entity Culling

Modernfix (Will not work with some mods but does give a bit of a boost)

Memory Leak (Fixes memory leaks in the client) 

GPU leak fix (same idea for the GPU)

