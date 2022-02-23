TrueSkillThroughTime.jl/.git:
	#git submodule add -b gh-pages git@github.com:glandfried/TrueSkillThroughTime.jl.git
	git submodule update --init TrueSkillThroughTime.jl/

crear:
	make -C TrueSkillThroughTime.jl/doc/
	
publicar: crear TrueSkillThroughTime.jl/.git
	rsync -avrc --delete --exclude=.git --exclude=makefile --exclude=TrueSkillThroughTime.jl/ TrueSkillThroughTime.jl/doc/build/ ./ 
