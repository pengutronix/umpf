IMAGES        = images/umpf-relationships.svg

all: $(IMAGES)

%.svg: %.dia
	dia --export="$@" --filter=svg "$<"
