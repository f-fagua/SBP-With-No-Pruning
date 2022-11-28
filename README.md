<h1>Scriptable Build Pipeline With no Pruning</h1>

The SBP with no pruning is a custom version of the [Scriptable Build Pipeline](https://docs.unity3d.com/Packages/com.unity.scriptablebuildpipeline@1.19/manual/index.html) that allows users to disable the pruning when making the build.

<p>This custom version adds an option on the SBP preferences window to diable the pruning. That way, on their next build, the Build Cache (Library/BuildCache) won't be cleaned even if it surpasses the max size limit set.</p>

<h2>What is the purpose of an SBP with no cache pruning?</h2>

<p>The build cache folder can go under the radar for small projects. Yet, for large-scale projects that target several build platforms, it could grow up to hundreds of GBs. When users limit its size, the SBP performs a file prune at the end of the build; it deletes the oldest build artifacts until it gets below the max size again.</p>

<p>The prune is a nice feature because it helps you optimize disk usage. Yet as it discards some build artifacts, whenever those are needed again, the system will register a cache-miss and rebuild those artifacts. In that case, the build times will increase.</p>

<p>On small projects, this might be fine. But it is a different story in large projects that target several platforms. Each target platform will produce different build artifacts for each asset on each platform. So, if your build pipeline discards the Android artifacts, the next time you build for that platform, it will take the same time as the first build you made.</p>

<p>By disabling the prunning, you will favor the build time at the cost of the disk usage of your build machine. If it is a trade-off you can afford, you might like this custom version of the SBP.</p>

<h2>Repository content</h2>

<p>Sample project with ta custom SBP package.</p>

<h2>How to use it</h2>

<ol>
	<li>Copy the SBP package on your project's Packages folder.</li>
	<li>Open the SBP preferences.</li>
	<li>Check the <code>Disable Cache Pruning During Builds</code> option.</li>
</ol>
